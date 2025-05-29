```
EEquivGraphPE(in_dim=>out_dim; init=glorot_uniform, bias=true)
```

E(n)-等変位置エンコーディング層。

# 引数

  * `in_dim::Int`: 入力位置特徴の次元。
  * `out_dim::Int`: 出力位置特徴の次元。
  * `init`: ニューラルネットワークの初期化関数。
  * `bias::Bool`: エッジ特徴の次元。

# 例

```jldoctest
julia> in_dim_edge, out_dim = 2, 5
(2, 5)

julia> l = EEquivGraphPE(in_dim_edge=>out_dim)
EEquivGraphPE(2 => 5)
```

詳細は [`EEquivGraphConv`](@ref) を参照してください。
