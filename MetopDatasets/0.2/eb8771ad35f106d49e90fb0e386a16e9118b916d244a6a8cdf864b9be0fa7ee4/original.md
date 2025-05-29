```
data_record_type(header::MainProductHeader)::Type
```

Get the type of data record based on the main product header

# Example

```julia-repl
julia> file_pointer = open("ASCA_SZO_1B_M03_20230329063300Z_20230329063556Z_N_C_20230329081417Z")
julia> main_header = MetopDatasets.native_read(file_pointer, MainProductHeader)
julia> data_record_type(main_header)
ASCA_SZO_1B_V13
```
