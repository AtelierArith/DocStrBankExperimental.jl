```julia
expand_derivatives(O; ...)
expand_derivatives(O, simplify; occurrences)

```

TODO

# 例

```jldoctest

julia> @variables x y z k;

julia> f=k*(abs(x-y)/y-z)^2
k*((abs(x - y) / y - z)^2)

julia> Dx=Differential(x) # x に関して微分
(::Differential) (generic function with 2 methods)

julia> dfx=expand_derivatives(Dx(f))
(k*((2abs(x - y)) / y - 2z)*IfElse.ifelse(signbit(x - y), -1, 1)) / y
```
