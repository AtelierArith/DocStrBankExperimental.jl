```
DenseShadow
```

密な古典的シャドウを表す構造体（2^N x 2^N 行列）で、2N インデックスを持つ単一の ITensor として保存されます。

# フィールド

  * `shadow_data::ITensor`: 密なシャドウを表す 2N インデックスを持つ ITensor。
  * `N::Int`: サイト数（キュービット）。
  * `site_indices::Vector{Index{Int64}}`: サイトインデックスのベクター（長さ N）。

# コンストラクタ

`DenseShadow(shadow_data::ITensor, N::Int, site_indices::Vector{Index{Int64}})` は以下を検証します：

  * `site_indices` の長さは N であること。
  * `shadow_data` は正確に 2N インデックスを持つこと。
  * `shadow_data` の未プライムインデックスの集合が `site_indices` と一致すること。
  * `shadow_data` のプライムインデックスの集合が `map(prime, site_indices)` と一致すること。
