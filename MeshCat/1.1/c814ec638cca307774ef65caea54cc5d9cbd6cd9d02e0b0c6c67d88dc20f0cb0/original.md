Call the given function `f`, but intercept any `settransform!` or `setprop!` calls and apply them to the given animation at the given frame instead.

```julia
atframe(
    f,
    animation::MeshCat.Animation,
    frame::Integer
) -> MeshCat.Animation

```

Usage:

```
vis = Visualizer()
setobject!(vis[:cube], Rect(Vec(0.0, 0.0, 0.0), Vec(0.5, 0.5, 0.5)))

anim = Animation(vis)

# At frame 0, set the cube's position to be the origin
atframe(anim, 0) do
    settransform!(vis[:cube], Translation(0.0, 0.0, 0.0))
end

# At frame 30, set the cube's position to be [1, 0, 0]
atframe(anim, 30) do
    settransform!(vis[:cube], Translation(1.0, 0.0, 0.0))
end

setanimation!(vis, anim)
```
