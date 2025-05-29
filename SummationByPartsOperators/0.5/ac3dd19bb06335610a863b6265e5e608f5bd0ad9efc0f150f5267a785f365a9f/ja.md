```
MatrixDerivativeOperator{T <: Real}
MatrixDerivativeOperator(xmin, xmax, nodes, weights, D, accuracy_order, source)
```

スカラー型 `T` の非周期グリッド上の導関数演算子で、行列ベクトル積として導関数を計算します。この型は、行列形式で与えられた新しい演算子を簡単に実験できるように設計されています。

この型のインスタンスは、希望するグリッドの端点 `xmin`、`xmax` と、`nodes`、`weights`、および参照区間上の導関数演算子 `D::AbstractMatrix` を渡すことによって構築できます。`nodes` には参照区間の境界点が含まれていると仮定します。`source` は係数のソースであり、実験のために `nothing` にすることができます。
