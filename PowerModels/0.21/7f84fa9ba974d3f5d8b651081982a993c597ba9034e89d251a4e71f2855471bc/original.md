```
parse_file(io::String; import_all=false, validate=true)
parse_file(io::IO; import_all=false, validate=true, filetype="json")
```

Parse a file into a PowerModels data structure.

The supported file types are:

  * `.m`: a Matpower file
  * `.raw`: a PTI (PSS(R)E-v33)
  * `.json`: a PowerModels.jl JSON file

All fields from PTI files will be imported if `import_all` is true.

If `validate = true`, PowerModels will validate the imported data for correctness.
