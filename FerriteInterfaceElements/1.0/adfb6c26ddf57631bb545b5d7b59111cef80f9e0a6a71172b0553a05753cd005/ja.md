```
InterfaceCellValues([::Type{T},] qr::QuadratureRule, func_ip::InterfaceCellInterpolation, [geom_ip::InterfaceCellInterpolation]; use_same_cv=true)
```

`InterfaceCellValues`は、`InterfaceCell`の各ファセットに対して1つずつの2つの`CellValues`に基づいています。同じ`CellValues`を両側で使用できるため、デフォルトではパフォーマンス向上のために同じオブジェクトが使用されます。必要に応じて、キーワード引数`use_same_cv`を`false`に設定することで、この動作を無効にできます。

# フィールド

  * `ip::InterfaceCellInterpolation`: インターフェース上の補間
  * `here::CellValues`: ファセット「ここ」の値
  * `there::CellValues`: ファセット「そこ」の値
  * `base_indices_here::Vector{Int}`: ファセット「ここ」の基底関数インデックス
  * `base_indices_there::Vector{Int}`: ファセット「そこ」の基底関数インデックス
  * `sides_and_baseindices::Tuple`: `InterfaceCellValues`の各基底関数に対する基底`CellValues`のサイドと基底関数
