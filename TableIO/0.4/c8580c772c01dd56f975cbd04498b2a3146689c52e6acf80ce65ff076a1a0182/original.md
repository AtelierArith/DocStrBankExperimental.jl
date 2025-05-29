```
read_table(file_picker:: Dict, args...; kwargs...)
```

Reading tabular data from a PlutoUI.jl FilePicker.

Usage (in a Pluto.jl notebook):

```
using PlutoUI, TableIO, DataFrames
using XLSX # import the packages required for the uploaded file formats
@bind f PlutoUI.FilePicker()
df = DataFrame(read_table(f); copycols=false)
```
