```
Train(file, type = :YAML)
```

Train is a datastruture for calculation context. The function Train() will create a train to use in calculations. Supported formats for the YAML files are: railtoolkit/schema (2022.05)

# Example

```
julia> my_train = Train("file.yaml") # will generate a train from a YAML file.
Train(variables)
```
