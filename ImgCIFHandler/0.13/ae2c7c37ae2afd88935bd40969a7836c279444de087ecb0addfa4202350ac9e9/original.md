```
imgload(handle,::Val{:HDF};path="/";frame=1)
```

Read a 2D HDF5 image from file `handle` located at HDF5 location `path`, returning only frame number `frame`, counting from 1
