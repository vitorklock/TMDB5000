
# Análise do Dataset [TMDB 5000 Movies](https://www.kaggle.com/datasets/tmdb/tmdb-movie-metadata)

Utilizamos VSCode combinado com a [extensão oficial do Jupyter Notebook](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter).

O Python utilizado é o Pyhon3 padrão do Ubuntu 20.04 LTS.

## Acessando o ambiente
### Scripts bash
Criamos os seguintes scripts, colocados no seu .bashrc, ou equivalente, para permitir a criação e acesso de [virtualenv](https://virtualenv.pypa.io/en/latest/)'s.

```bash
# Function to create and activate a virtual environment in ~/.virtualenvs
mkvenv() {
  if [ -z "$1" ]; then
    echo "Please provide a name for the virtual environment."
    return 1
  fi

  VENV_PATH="$HOME/.virtualenvs/$1"

  # Create the directory if it doesn't exist
  mkdir -p "$HOME/.virtualenvs"

  # Create the virtual environment
  virtualenv "$VENV_PATH"

  # Activate the virtual environment
  source "$VENV_PATH/bin/activate"

  echo "Virtual environment '$1' created and activated."
}

# Function to activate an existing virtual environment from ~/.virtualenvs
useenv() {
  if [ -z "$1" ]; then
    echo "Please provide the name of the virtual environment to activate."
    return 1
  fi

  VENV_PATH="$HOME/.virtualenvs/$1"

  # Check if the virtual environment exists
  if [ ! -d "$VENV_PATH" ]; then
    echo "Virtual environment '$1' not found in ~/.virtualenvs."
    return 1
  fi

  # Activate the virtual environment
  source "$VENV_PATH/bin/activate"

  echo "Virtual environment '$1' activated."
}
```

#### Utilização

Criando o ambiente pela primeira vez, chamado `movies`.
```bash
$ mkvenv movies
```

Acessando o ambiente
```bash
$ useenv movies
```

Saindo do ambiente 
```bash
$ deactivate
```