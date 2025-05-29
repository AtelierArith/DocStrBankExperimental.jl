```
plot_attractors_curves(attractors_cont, attractor_to_real [, prange]; kw...)
```

[`plot_basins_curves`](@ref) と同様ですが、バシンの割合ではなく、パラメータに対するアトラクタの依存性を視覚化します。関数 `attractor_to_real` は `StateSpaceSet`（アトラクタ）を入力として受け取り、パラメータ軸に対してプロットできるように実数を返します。[`plot_basins_attractors_curves`](@ref) も参照してください。

[`plot_continuation_curves`](@ref) と同じキーワード。
