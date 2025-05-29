```
get_preconditioner(amp::AbstractManoptProblem, p, X)
```

評価する対称的で正定値の前処理器（コスト関数 `f` のヘッセ行列の逆の近似）を、点 `p` での [`AbstractManoptProblem`](@ref) `amp` の目的に対して接ベクトル `X` に適用します。
