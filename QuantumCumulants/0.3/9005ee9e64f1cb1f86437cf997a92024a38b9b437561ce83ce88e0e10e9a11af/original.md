```
Spin <: QSym
```

Spin operator on a [`SpinSpace`](@ref) representing the Spin-operators Sx, Sy and Sz for collective spin systems.  The field axis represents x, y and z as 1, 2 and 3, repectively. The operators follow the rules for angular momentum operators: [Sj,Sk] = i⋅∑ϵjkl⋅Sl

# Examples

```
julia> h = SpinSpace("Spin-N/2")
ℋ(Spin-N/2)

julia> Sx = Spin(h,:S,1)
Sx
```
