```
setGPUID!(tsg::TasmanianSG, GPUID)
```

when using cuda on a machine with multiple GPUs, this helps set the GPU for this grid NOTE: each instance of the sparse grids class holds a separate       instance of GPUID and different grids can be assigned to       different GPUs (on multi-gpu system) GPUID can be changed at any time, however, this will cause some of the internal cache to be invalidated and it may lead to extraneous data movement

calling read or make***Grid will reset the selected GPU

defaults to 0

this doesn't do anything unless enableAcceleration is called using a "gpu-" acceleration type
