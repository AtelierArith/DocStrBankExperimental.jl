```
nProcX,nProcY,nProcZ, xc,yc,zc, nNodeX,nNodeY,nNodeZ = get_processor_partitioning(filename; is64bit=false)
```

Reads a LaMEM processor partitioning file, used to create marker files, and returns the parallel layout. By default this is done for a 32bit PETSc installation, which will fail if you actually use a 64bit version.
