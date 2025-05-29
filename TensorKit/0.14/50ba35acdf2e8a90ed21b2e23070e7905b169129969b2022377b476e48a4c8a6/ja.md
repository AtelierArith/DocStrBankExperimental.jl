```
rightorth(t::AbstractTensorMap, (leftind, rightind)::Index2Tuple;
            alg::OrthogonalFactorizationAlgorithm = LQpos()) -> L, Q
```

インデックス `rightind` に対する直交基底 `Q` を作成し、`permute(t, (leftind, rightind)) = L*Q` となるように残りの `L` を作成します。

`leftind` と `rightind` が指定されていない場合、`t` の現在の左インデックスと右インデックスの分割が使用されます。その場合、`rightorth!(t, alg = LQpos())` を使用することで、`t` 内のデータが破壊/上書きされることを許可すると、より少ないメモリが割り当てられます。

利用可能な異なるアルゴリズムには、`LQ()`, `LQpos()`, `RQ()`, `RQpos()`, `SVD()` および `Polar()` があります。`LQ()` と `LQpos()` は下三角行列 `L` を生成し、転置のQR分解を使用して計算されます。`RQ()` と `RQpos()` は上三角の残りの `L` を生成し、左の次元の合計が右の次元の合計以下である場合にのみ機能します。`LQpos()` と `RQpos()` は、`L` の対角要素が正であるように追加の補正を加えます。`Polar()` はエルミートかつ正半定値の `L` を生成します。`LQpos()`, `RQpos()` および `Polar()` のみが一意であり（残余の自由度なし）、同じ入力テンソル `t` に対して常に同じ結果を返します。

直交性には `InnerProductStyle(t) <: HasInnerProduct` が必要であり、`rightorth(!)` は現在 `InnerProductStyle(t) === EuclideanInnerProduct()` のみで実装されています。
