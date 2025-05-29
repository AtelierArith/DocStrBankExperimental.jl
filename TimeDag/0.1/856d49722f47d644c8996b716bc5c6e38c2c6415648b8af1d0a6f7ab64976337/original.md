```
tea_file(path::AbstractString, value_field_name)
```

Get a node that will read data from the tea file at `path`.

Such a tea file must observe the following properties, which will be verified at runtime:

  * Have a primary time field which is compatible with a Julia `DateTime`.
  * Have exactly one column with name `value_field_name`.
  * Have *strictly* increasing times.

Upon node creation, the metadata section of the file will be parsed to infer the value type of the resulting node. However, the bulk of the data will only be read at evaluation time.

# See also

  * The [tea file spec](http://discretelogics.com/resources/teafilespec/)
  * [TeaFiles.jl](https://github.com/tpgillam/TeaFiles.jl)
