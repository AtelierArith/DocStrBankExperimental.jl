```
build_config(data_dir::String, config_file::String)
```

Interactively guides user through writing a configuration YAML file for DeIdentification. The `data_dir` should contain one of each type of dataset you expect to deidentify (e.g. the data directory `./test/data'` contains `pat.csv`, `med.csv`, and `dx.csv`). The config builder reads the headers of each CSV file and iteratively asks about the output name and deidentification type of each column. The results are written to `config_file`.
