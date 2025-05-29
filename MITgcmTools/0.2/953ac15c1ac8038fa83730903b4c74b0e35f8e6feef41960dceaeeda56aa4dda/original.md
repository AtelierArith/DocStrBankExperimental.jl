```
read_bin(fil::String,kt::Union{Int,Missing},kk::Union{Int,Missing},prec::DataType,mygrid::gcmgrid)
```

Read model output from binary file and convert to MeshArray. Other methods:

```
read_bin(fil::String,prec::DataType,mygrid::gcmgrid)
read_bin(fil::String,mygrid::gcmgrid)
```
