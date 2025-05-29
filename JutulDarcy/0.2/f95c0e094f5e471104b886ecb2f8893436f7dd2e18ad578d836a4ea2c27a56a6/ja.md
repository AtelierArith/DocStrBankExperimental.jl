```
mask = PerforationMask(mask::Vector)
```

穿孔マスクを作成します。これは、`mask`引数の下で井戸に対して[`setup_forces`](@ref)に渡すことができます。マスクは井戸の穿孔の数と等しく、参照井戸インデックスに対して乗法的に適用されます。たとえば、`:Injector`という名前の井戸に2つの穿孔がある場合、次のマスクは最初の穿孔を無効にし、2番目の穿孔の接続強度を50%減少させます。

```julia
mask = PerforationMask([0.0, 0.5])
iforces = setup_forces(W, mask = mask)
forces = setup_reservoir_forces(model, control = controls, Injector = iforces)
```
