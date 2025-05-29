```
nonbacktrack_embedding(g::AGraph, k::Int)
```

`g`の非バックトラッキング行列のスペクトル埋め込み（[Krzakala et al.](http://www.pnas.org/content/110/52/20935.short)を参照）。

```
`g`: 入力グラフ
`k`: 埋め込む次元数
```

行列`ϕ`を返します。ここで`ϕ[:,i]`は頂点`i`の座標です。

注意: [`nonbacktracking_matrix`](@ref)を明示的に構築しません。詳細については[`nonbacktracking_matrix`](@ref)を参照してください。
