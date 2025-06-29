```
polar(angle, radius[, spec; kwargs...])
```

1つ以上の極座標プロットを描画します。

最初の座標は角度を表し、2番目は線の点の半径を表します。残りは線プロットと同様に定義されますが、最初の変数（`angle`）は常に必須です。（cf. [`plot`](@ref)）。

最初の変数はデフォルトでラジアンと見なされ、グリッドの角度ラベルはπの因子として表示されます。キーワード引数`radians = false`を使用して、角度を度で渡し、表示します。

!!! note
    極座標プロットでは対数スケールおよび逆スケールは無効です


# 例

```julia
# サンプルデータを作成
angles = LinRange(0, 360, 40)
radii = LinRange(0, 2, 40)
# 度で極座標プロットを描画
polar(angles, radii, radians=false)

```
