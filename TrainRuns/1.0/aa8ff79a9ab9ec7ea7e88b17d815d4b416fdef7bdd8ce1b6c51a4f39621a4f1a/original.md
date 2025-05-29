```
Settings(file)
```

Settings is a datastruture for calculation context. The function Settings() will create a set of settings for the train run calculation. `file` is optinal may be used to load settings in the YAML format.

# Example

```
julia> my_settings = Settings() # will generate default settings
# massModel, stepVariable, stepSize, approxLevel, outputDetail, outputFormat
Settings(:mass_point, :distance, 20, 3, :running_time, :dataframe)
```
