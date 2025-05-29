```
generate_sprinkling(manifold, boundary, count[; preset_atoms = [], rng = default_rng()]) -> Vector{Coordinates}
```

境界 `boundary` に `manifold` 上で `count` の時空間原子を散布します。散布密度は多様体の体積要素 $\sqrt{-g}$ に比例します。

返される座標は常に時間座標によってソートされており、$x_i \preceq x_j$ は $i \leq j$ の場合にのみ真となります。このパッケージのいくつかのコード最適化はこの順序に依存しています。

`preset_atoms` を介して1つ以上の座標点が渡されると、それらは生成された散布に常に存在します。さらに、カスタム乱数生成器を使用したい場合（例えば、シードを指定するため）には、`rng` パラメータを指定できます。
