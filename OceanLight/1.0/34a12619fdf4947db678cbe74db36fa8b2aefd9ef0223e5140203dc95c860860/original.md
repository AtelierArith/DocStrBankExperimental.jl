```
exported(ed::Array{<:Real,3},η::Array{<:Real,2},p::Param,
              fname::String,mode="2D"::String,nk=0::Int64)
```

exported the irradiance data into `fname`.h5 file. 

There are 3 modes of exporting the data: `2D`, `3D`, and `full`. If not specified the mode will automatically set to `2D`. 
