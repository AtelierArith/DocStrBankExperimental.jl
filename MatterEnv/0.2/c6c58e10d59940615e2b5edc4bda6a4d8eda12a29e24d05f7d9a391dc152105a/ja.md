```
射影
```

波動関数の射影のデータ型。

# フィールド

  * `number_kpoints::Integer`: k点の数を格納します
  * `number_bands::Integer`: バンドの数を格納します
  * `number_ions::Integer`: イオンの数を格納します
  * `projection::Array{<:Complex, 4}`: 射影 ⟨Yₗₘ|ϕₙₖ⟩ を格納します。インデックスの順序は [k点番号、バンド番号、イオン番号、軌道番号] です
  * `projection_square::Array{<:Real, 4}`: 二乗射影 |⟨Yₗₘ|ϕₙₖ⟩|² を格納します。インデックスの順序は `projection` と同じです。
