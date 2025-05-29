```
@cushow(ex)
```

GPU analog of `Base.@show`. It comes with the same type restrictions as [`@cuprintf`](@ref).

```julia
@cushow threadIdx().x
```
