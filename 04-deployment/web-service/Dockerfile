FROM python:3.9.7-slim

COPY [ "pyproject.toml", "poetry.lock", "./" ]

# RUN curl -sSL https://raw.githubusercontent.com/python-poetry/poetry/master/get-poetry.py|python

RUN pip install -U pip
RUN pip install poetry

WORKDIR /app

RUN poetry config virtualenvs.create false
RUN poetry install --no-interaction

#RUN pipenv install --system --deploy
COPY [ "predict.py", "lin_reg.bin", "./" ]

EXPOSE 9696

ENTRYPOINT [ "gunicorn", "--bind=0.0.0.0:9696", "predict:app"]