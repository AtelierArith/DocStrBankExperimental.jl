```
`update!(p::Scene)`
```

`Scene` とそのすべての子を更新します。更新は、すべてのシーンに対して次の操作を実行します：

```julia
if !scene.raw[]
    scene.update_limits[] && update_limits!(scene)
    scene.scale_plot[] && scale_scene!(scene)
    scene.center[] && center!(scene)
end
```
