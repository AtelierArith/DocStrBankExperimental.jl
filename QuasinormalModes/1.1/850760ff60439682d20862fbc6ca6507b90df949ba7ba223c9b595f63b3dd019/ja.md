```
AIMCache(p::QuadraticEigenvalueProblem{N,T}) where {N <: Unsigned, T <: Number}
```

二次固有値問題に適したAIMCacheオブジェクトを作成します。

# 入力

  * `p::QuadraticEigenvalueProblem`: 問題データ。

# 出力

`AIMCache{N,Polynomial{T}}`オブジェクト。 ```
