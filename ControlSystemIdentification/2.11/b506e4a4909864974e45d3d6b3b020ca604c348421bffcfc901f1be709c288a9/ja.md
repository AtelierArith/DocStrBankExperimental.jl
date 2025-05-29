```
model = arma(d::AbstractIdData, na, nc; initial_order=20, method=:ls)
```

`na`係数を分母に、`nc`係数を分子に持つ自己回帰移動平均モデルを推定します。モデルとシステムを駆動する推定されたノイズ系列を返します。

# 引数:

  * `d`: iddata
  * `initial_order`: この次数の初期ARモデルが残差を推定するために使用されます
  * `estimator`: 関数 `(A,y)->minimizeₓ(Ax-y)` デフォルトは `\` ですが、別のオプションは `wtls_estimator(1:length(y)-initial_order,na,nc,ones(nc))` です

[`estimate_residuals`](@ref) も参照してください
