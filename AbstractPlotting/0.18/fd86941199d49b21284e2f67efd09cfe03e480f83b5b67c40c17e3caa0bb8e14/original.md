```
`update!(p::Scene)`
```

Updates a `Scene` and all its children. Update will perform the following operations for every scene:

```julia
if !scene.raw[]
    scene.update_limits[] && update_limits!(scene)
    scene.scale_plot[] && scale_scene!(scene)
    scene.center[] && center!(scene)
end
```
