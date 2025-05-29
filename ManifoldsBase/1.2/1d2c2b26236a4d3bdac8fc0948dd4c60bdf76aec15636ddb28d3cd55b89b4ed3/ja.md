```
NLSolveInverseRetraction{T<:AbstractRetractionMethod,TV,TK} <:
    ApproximateInverseRetraction
```

逆射影法を用いて射影の逆を近似するための逆射影法です。

# コンストラクタ

```
NLSolveInverseRetraction(
    method::AbstractRetractionMethod[, X0];
    project_tangent=false,
    project_point=false,
    nlsolve_kwargs...,
)
```

初期推定 `X0` を持つ射影 `method` の近似逆射影を構築します。デフォルトはゼロベクトルです。`project_tangent` が `true` の場合、射影の前に接ベクトルが `project` を使用して射影されます。`project_point` が `true` の場合、射影の後に結果の点が射影されます。`nlsolve_kwargs` は `NLsolve.nlsolve` に渡されるキーワード引数です。
