```
leftnull(t::AbstractTensor, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = QRpos()) -> N
```

インデックス `leftind` のサポートの直交補空間のための正規直交基底を作成します。これにより、`N' * permute(t, (leftind, rightind)) = 0` となります。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`leftnull!(t, alg = QRpos())` を使用することで、`t` 内のデータが破壊/上書きされることを許可すると、より少ないメモリが割り当てられます。

利用可能な異なるアルゴリズムには、`QR()`（または同等の `QRpos()`）、`SVD()`、および `SDD()` があります。最初のものは行列がフルランクであると仮定し、`iszero(atol)` および `iszero(rtol)` を要求します。`SVD()` および `SDD()` を使用する場合、`rightnull` は対応する特異値分解を使用し、どの特異値をゼロと見なすかの絶対または相対的な許容誤差を指定できます。このとき、`max(atol, norm(t)*rtol)` が上限として使用されます。

直交性には `InnerProductStyle(t) <: HasInnerProduct` が必要であり、`leftnull(!)` は現在 `InnerProductStyle(t) === EuclideanInnerProduct()` のみで実装されています。
