```
position_to_site(sys::System, r)
```

位置 `r` を [`Site`](@ref) の4つのインデックスに変換します。`r` の座標は元の結晶の格子ベクトルの単位で与えられます。この関数は、[`reshape_supercell`](@ref) を使用して形状を変更したシステムで作業する際に便利です。

# 例

```julia
# 最初の格子ベクトルの4倍だけずれた単位セルの中心にある `site` を見つける
site = position_to_site(sys, [4.5, 0.5, 0.5])

# このサイトの双極子を印刷する
println(sys.dipoles[site])
```
