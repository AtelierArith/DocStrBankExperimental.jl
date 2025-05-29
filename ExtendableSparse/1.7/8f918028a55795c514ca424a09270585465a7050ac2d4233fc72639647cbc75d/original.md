```
MKLPardisoLU(;iparm::Vector, mtype::Int)

MKLPardisoLU(matrix; iparm, mtype)
```

LU factorization based on pardiso. For using this, you need to issue `using Pardiso`. This version  uses the early 2000's fork in Intel's MKL library.

The optional keyword arguments `mtype` and `iparm`  are   [Pardiso internal parameters](https://github.com/JuliaSparse/Pardiso.jl#readme).

For setting them you can also access the `PardisoSolver` e.g. like

```
using Pardiso
plu=MKLPardisoLU()
Pardiso.set_iparm!(plu.ps,5,13.0)
```
