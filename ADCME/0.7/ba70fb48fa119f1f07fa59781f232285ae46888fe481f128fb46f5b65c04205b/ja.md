```
mpi_gather(u::Union{Array{Float64, 1}, PyObject}, deps::Union{Missing, PyObject} = missing)
```

異なるプロセスからルートプロセスにすべてのベクトルを集めます。この関数は、プロセスIDの順序でローカルベクトルを連結した長いベクトルを返します。
