```
PardisoLU(;iparm::Vector, 
           dparm::Vector, 
           mtype::Int)

PardisoLU(matrix; iparm,dparm,mtype)
```

LU factorization based on pardiso. For using this, you need to issue `using Pardiso` and have the pardiso library from  [pardiso-project.org](https://pardiso-project.org)  [installed](https://github.com/JuliaSparse/Pardiso.jl#pardiso-60).

The optional keyword arguments `mtype`, `iparm`  and `dparm` are  [Pardiso internal parameters](https://github.com/JuliaSparse/Pardiso.jl#readme).

Forsetting them, one can also access the `PardisoSolver` e.g. like

```
using Pardiso
plu=PardisoLU()
Pardiso.set_iparm!(plu.ps,5,13.0)
```
