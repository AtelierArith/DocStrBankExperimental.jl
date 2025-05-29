```
AIMCache(p::NumericAIMProblem{N,T}) where {N <: Unsigned, T <: Number}
```

数値固有値問題に適したAIMCacheオブジェクトを作成します。

# 入力

  * `p::NumericAIMProblem`: 問題データ。

# 出力

`AIMCache{N,T}`オブジェクト。
