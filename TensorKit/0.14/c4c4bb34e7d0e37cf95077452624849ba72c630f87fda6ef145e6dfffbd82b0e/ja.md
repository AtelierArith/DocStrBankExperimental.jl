```
leftorth(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = QRpos()) -> Q, R
```

インデックス `leftind` のための直交正規基底 `Q` を作成し、`permute(t, (leftind, rightind)) = Q*R` となるように残りの `R` を作成します。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`leftorth!(t, alg = QRpos())` を使用することで、`t` 内のデータが破壊/上書きされることを許可すれば、より少ないメモリが割り当てられます。

利用可能な異なるアルゴリズムには、`QR()`, `QRpos()`, `SVD()` および `Polar()` があります。`QR()` と `QRpos()` は標準的なQR分解を使用し、上三角行列 `R` を生成します。`Polar()` はエルミートかつ正定値の `R` を生成します。`QRpos()` は標準的なQR分解を修正し、`R` の対角要素が正になるようにします。`QRpos()` と `Polar()` のみがユニークであり（残余自由度なし）、同じ入力テンソル `t` に対して常に同じ結果を返します。

直交性には `InnerProductStyle(t) <: HasInnerProduct` が必要であり、`leftorth(!)` は現在 `InnerProductStyle(t) === EuclideanInnerProduct()` のみで実装されています。
