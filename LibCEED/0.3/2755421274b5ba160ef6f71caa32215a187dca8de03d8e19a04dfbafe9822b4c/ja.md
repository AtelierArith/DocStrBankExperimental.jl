```
apply!(b::Basis, nelem, tmode::TransposeMode, emode::EvalMode, u::AbstractCeedVector, v::AbstractCeedVector)
```

ノードから四分点への基底評価を適用するか、その逆を行い、結果を[`CeedVector`](@ref) `v`に格納します。

`nelem`は基底評価を適用する要素の数を指定します。バックエンドはCeedElemRestrictionCreateBlocked()での順序を指定します。

`tmode`を`CEED_NOTRANSPOSE`に設定するとノードから四分点への評価が行われ、`CEED_TRANSPOSE`に設定すると転置が適用され、四分点からノードへのマッピングが行われます。

[`EvalMode`](@ref) `emode`を次のように設定します：

  * `CEED_EVAL_NONE`は値を直接使用するため、
  * `CEED_EVAL_INTERP`は補間された値を使用するため、
  * `CEED_EVAL_GRAD`は勾配を使用するため、
  * `CEED_EVAL_WEIGHT`は四分点の重みを使用するため。
