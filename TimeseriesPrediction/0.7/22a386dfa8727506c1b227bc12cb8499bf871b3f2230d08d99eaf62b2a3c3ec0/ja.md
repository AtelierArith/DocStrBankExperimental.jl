```
MSEp(R::AbstractDataset{D,T}, R_test, p; method, ntype, stepsize) -> error
```

テストセット `R_test` を使用して長さ `p` の反復予測の平均二乗誤差を計算します。

## 説明

この誤差測定は、`R`、`method`、`ntype`、および `stepsize` からなる予測モデルを受け取り、その性能を評価します。テストセット `R_test` は、`R` と同じ遅延 `τ` および次元 `D` を持つ遅延再構成です。長さ `p` の `R_test` の各サブセットに対して `localmodel_tsp` を呼び出します。モデル誤差は次のように定義されます。

$$
\begin{aligned}
MSE_p = \frac{1}{p|T_{ref}|}\sum_{t\in T_{ref}}\sum_{i=1}^{p} \left(y_{t+i}
- y_{pred,t+i} \right)^2
\end{aligned}
$$

ここで $|T_{ref}|$ は使用される `R_test` のサブセットの数です。

## 参考文献

[`localmodel_tsp`](@ref) を参照してください。
