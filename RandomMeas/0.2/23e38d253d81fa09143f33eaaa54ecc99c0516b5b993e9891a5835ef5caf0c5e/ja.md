```
FactorizedShadow
```

因子化された古典的シャドウを表す構造体で、単一量子ビットシャドウのテンソル積として表現できます。

# フィールド

  * `shadow_data::Vector{ITensor}`: 各量子ビット/サイトのシャドウを表すITensorのベクトル（各2×2）。
  * `N::Int`: 量子ビット/サイトの数。
  * `site_indices::Vector{Index{Int64}}`: サイトインデックスのベクトル（長さN）。

# コンストラクタ

`FactorizedShadow(shadow_data::Vector{ITensor}, N::Int, site_indices::Vector{Index{Int64}})` は以下を検証します：

  * `shadow_data` と `site_indices` の長さが `N` に等しいこと。
  * `shadow_data` の各ITensorが正確に2つのインデックスを持ち、対応する未プライムおよびプライムのサイトインデックスを含むこと。
