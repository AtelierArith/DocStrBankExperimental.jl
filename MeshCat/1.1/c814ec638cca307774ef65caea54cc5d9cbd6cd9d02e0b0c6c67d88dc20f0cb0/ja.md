与えられた関数 `f` を呼び出しますが、`settransform!` または `setprop!` の呼び出しを intercept し、それらを指定されたフレームの指定されたアニメーションに適用します。

```julia
atframe(
    f,
    animation::MeshCat.Animation,
    frame::Integer
) -> MeshCat.Animation

```

使用法:

```
vis = Visualizer()
setobject!(vis[:cube], Rect(Vec(0.0, 0.0, 0.0), Vec(0.5, 0.5, 0.5)))

anim = Animation(vis)

# フレーム 0 で、キューブの位置を原点に設定
atframe(anim, 0) do
    settransform!(vis[:cube], Translation(0.0, 0.0, 0.0))
end

# フレーム 30 で、キューブの位置を [1, 0, 0] に設定
atframe(anim, 30) do
    settransform!(vis[:cube], Translation(1.0, 0.0, 0.0))
end

setanimation!(vis, anim)
```
