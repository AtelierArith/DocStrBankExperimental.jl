```
@cushow(ex)
```

`Base.@show`のGPUアナログです。[`@cuprintf`](@ref)と同じ型制限があります。

```julia
@cushow threadIdx().x
```
