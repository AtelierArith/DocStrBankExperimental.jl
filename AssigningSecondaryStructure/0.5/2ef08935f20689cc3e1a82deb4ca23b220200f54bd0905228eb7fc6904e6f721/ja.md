```
assign_secondary_structure(chain_backbone::Array{T,3}}) where T<:Real
assign_secondary_structure(chain_backbones::Vector{Array{T,3}}) where T<:Real
```

与えられたチェーンバックボーンのベクトルは、それぞれ3x3xLのサイズの3次元配列として表され、この関数は各残基に二次構造を割り当てます。

対応するチェーンとそれぞれの残基に対する二次構造の割り当てを含む整数のベクトルのベクトルを返します。二次構造は以下のようにエンコードされています：

  * `1`: ループ（ヘリックスでもストランドでもない）
  * `2`: ヘリックス；α、3_10、またはπ
  * `3`: ストランド；βシートの一部
