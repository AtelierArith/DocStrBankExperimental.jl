```
rightnull(t::AbstractTensor, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = LQ(),
            atol::Real = 0.0,
            rtol::Real = eps(real(float(one(scalartype(t)))))*iszero(atol)) -> N
```

インデックス `rightind` のサポートの直交補空間のための直交正規基底を作成します。これにより、`permute(t, (leftind, rightind))*N' = 0` となります。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`rightnull!(t, alg = LQpos())` を使用することで、`t` 内のデータが破壊/上書きされることを許可すれば、より少ないメモリが割り当てられます。

利用可能な異なるアルゴリズムには、`LQ()`（または同等の `LQpos`）、`SVD()`、および `SDD()` があります。最初のものは行列がフルランクであると仮定し、`iszero(atol)` と `iszero(rtol)` を要求します。`SVD()` と `SDD()` を使用する場合、`rightnull` は対応する特異値分解を使用し、どの特異値をゼロと見なすかの絶対または相対的な許容誤差を指定できます。このとき、`max(atol, norm(t)*rtol)` が上限として使用されます。

直交性には `InnerProductStyle(t) <: HasInnerProduct` が必要であり、`rightnull(!)` は現在 `InnerProductStyle(t) === EuclideanInnerProduct()` のみで実装されています。
