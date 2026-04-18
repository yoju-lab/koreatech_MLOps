FROM python:3.11-slim

RUN apt-get update && apt-get install -y \
    curl \
    wget \
    git \
    lsof \
    procps \
    && rm -rf /var/lib/apt/lists/*

# Python 패키지 설치
RUN pip install --no-cache-dir --upgrade pip

# 작업 디렉토리 설정
WORKDIR /apps

# Clone the Git repository.
RUN git clone https://github.com/yoju-lab/koreatech_MLOps

# Changes the working directory to /apps/${REPO_NAME}. This uses the variable to dynamically set the directory path.
WORKDIR /apps/koreatech_MLOps

# RUN pip install --no-cache-dir -r ./requirements.txt
RUN pip install --no-cache-dir -r ./app/requirements.txt

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]