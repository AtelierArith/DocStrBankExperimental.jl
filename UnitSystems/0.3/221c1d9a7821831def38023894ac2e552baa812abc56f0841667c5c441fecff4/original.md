```Julia
dyne(U::UnitSystem) = force(𝟏,U,Gauss)
```

Historical `dyne` unit of `force` (N or lb).

```Julia
julia> dyne(Metric) # N
1.0e-5

julia> dyne(CGS) # dyn
1

julia> dyne(English) # lb
2.2480894309971053e-6

julia> dyne(FPS) # pdl
7.233013851209895e-5

julia> dyne(Engineering) # kp
1.0197162129779282e-6
```
