```
copyGrid(tsg::TasmanianSG, outputs_begin = 0, outputs_end = -1)
```

accepts an instance of TasmanianSparseGrid class and creates a hard copy of the class and all included data original class is not modified

tsg: instance of TasmanianSG      the source for the copy

outputs_begin: integer indicating the first output to copy

outputs*end: integer one bigger than the last output to copy             if set to -1, all outputs from outputs*begin to             the end will be copied

Examples:

copyGrid(other, 0, -1) # copy all outputs (default) copyGrid(other, 0, getNumOutputs(other)) # also copy all copyGrid(other, 0, 3) # copy outputs 0, 1, and 2 copyGrid(other, 1, 4) # copy outputs 1, 2, and 3
