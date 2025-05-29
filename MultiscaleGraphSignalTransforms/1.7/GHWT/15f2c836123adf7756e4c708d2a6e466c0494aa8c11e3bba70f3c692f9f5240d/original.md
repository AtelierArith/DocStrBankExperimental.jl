```
ghwt_core!(GP::GraphPart)
```

performs the forward GHWT transform, which computes tag and compinfo of GP, but not the expansion coefficients.

### Input Arguments

  * `GP::GraphPart`: a GraphPart object (with or without tag and compinfo data); note that tag and compinfo will be modified after this function is executed
