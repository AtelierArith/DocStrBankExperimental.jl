```Julia
newton(U::UnitSystem) = force(𝟏,U,Metric)
```

Metric `newton` unit of `force` (N or lb).

```Julia
julia> newton(Metric) # N
1

julia> newton(CGS) # dyn
99999.99999999999

julia> newton(English) # lb
0.2248089430997105

julia> newton(FPS) # pdl
7.233013851209893

julia> newton(Engineering) # kp
0.10197162129779283
```
