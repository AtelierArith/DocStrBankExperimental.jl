```
jumpratelaw(rx; combinatoric_ratelaw=true)
```

与えられた [`Reaction`](@ref) に対して、反応のために生成された確率的化学動力学モデル SSA で使用される記号反応速度法則を返します。次のように定義された反応の場合

`k*X*Y, X+Z --> 2X + Y`

返される式は `k*X^2*Y*Z` になります。次の形式の反応の場合

`k, 2X+3Y --> Z`

返される式は `k * binomial(X,2) * binomial(Y,3)` になります。

注意:

  * アロケート
  * `combinatoric_ratelaw=true` は速度法則の計算に二項係数を使用します。つまり、`2S -> 0` の速度 `k` の場合、速度法則は `k*S*(S-1)/2` になります。`combinatoric_ratelaw=false` の場合、速度法則は `k*S*(S-1)` になり、すなわち速度法則はスケーリング因子で正規化されません。
