Intermediate CG state variables to be used inside cg and cg!. `u`, `r` and `c` should be of the same type as the solution of `cg` or `cg!`.

```
struct CGStateVariables{T,Tx<:AbstractArray{T}}
    u::Tx
    r::Tx
    c::Tx
end
```
