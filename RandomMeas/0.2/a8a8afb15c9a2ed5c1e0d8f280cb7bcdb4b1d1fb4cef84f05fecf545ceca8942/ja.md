```
ShallowShadow
```

浅い古典的シャドウを表す構造体で、MPO ITensorオブジェクトとして保存されます。

# フィールド

  * `shadow_data::MPOr`: 浅いシャドウを表すMPO。
  * `N::Int`: サイト数（キュービット）。
  * `site_indices::Vector{Index{Int64}}`: サイトインデックスのベクター（長さN）。

# コンストラクタ

`ShallowShadow(shadow_data::MPO, N::Int, site_indices::Vector{Index{Int64}})` は以下を検証します：

  * `site_indices` の長さがNであること。
  * `shadow_data` が正確にN個のテンソルを持ち、サイトインデックスがsite_indicesと一致すること。
