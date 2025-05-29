```
eigh(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple) -> D, V
```

テンソル `t` の固有値因子分解を、`rightind` から `leftind` への線形写像として計算します。関数 `eigh` は、線形写像がエルミートであることを前提としており、`D` と `V` は `t` と同じ `scalartype` を持つテンソルです。非エルミートテンソルについては `eig` と `eigen` を参照してください。エルミート性は、テンソルが内積空間上で作用することを要求し、現在の実装では `InnerProductStyle(t) === EuclideanInnerProduct()` である必要があります。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`eigh!(t)` を使用することで、`t` 内のデータが破壊/上書きされることを許可すれば、より少ないメモリが割り当てられます。`eigh!` が呼び出される順列テンソルは、ドメインとコドメインが等しい必要があり、そうでない場合、固有値分解は無意味であり、次の式を満たすことはできません。

```
permute(t, (leftind, rightind)) * V = V * D
```

`eigen` と `eig` も参照してください。
