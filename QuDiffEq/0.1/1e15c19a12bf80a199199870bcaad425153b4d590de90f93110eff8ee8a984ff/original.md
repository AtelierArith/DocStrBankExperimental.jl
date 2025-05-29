```
TaylorParam(k::Int, t::L, H::Matrix, x::Array{CPType,1})

TaylorParam(k::Int,t::L,prob::QuLDEProblem{uType, tType, isinplace, F, P, T})
```

Assigns values to parameters required for Taylor series based Hamiltonian simulation.

```
* k : sets order of Taylor series expansion
* t : time of evolution
* H : Hamiltonian
* x : intial vector
* prob : wrapper for Linear differential equation problems (contains H, x, b)
```
