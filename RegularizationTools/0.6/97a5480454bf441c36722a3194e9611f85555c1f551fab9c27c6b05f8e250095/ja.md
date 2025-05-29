```
function solve(
    Ψ::RegularizationProblem,
    b::AbstractVector;
    alg = :gcv_svd,
    method = Brent(),
    λ₁ = 0.0001,
    λ₂ = 1000.0,
    λ₀ = 1.0,
    kwargs...
)
```

最適な正則化パラメータ λ をアルゴリズム `alg` と最適化 `method` を使用して見つけます。アルゴリズムの選択肢は次のとおりです。

```
    :gcv_tr - トレース形式を使用した一般化交差検証（遅い）
    :gcv_svd - SVD分解を使用した一般化交差検証（速い）
    :L_curve - L-カーブアルゴリズム 
```

最適化手法は、Optimパッケージで利用可能なものです。境界で最適化する手法（`Brent()` と `GoldenSection()`）は、[λ₁, λ₂] を境界として使用します。他の手法は初期推測に λ₀ を使用します。`Brent()`（デフォルト）および `NelderMead()` の手法が推奨されます。追加のキーワード引数は最適化手法に渡されます。

!!! tip
    gcv*svdアルゴリズムは最も速く、最も安定しています。L*curveアルゴリズムは上限と下限に敏感です。良い解を得るために狭い上限と下限を指定してください。


solve関数は元のデータを受け取り、標準形式に変換し、指定された境界内で検索を行い、[RegularizatedSolution](@ref) を返します。

使用例（標準構文）

```julia
# Aは行列で、bは応答ベクトルです。 
Ψ = setupRegularizationProblem(A, 2)     # 問題を設定
sol = solve(Ψ, b)                        # 解く
```

使用例（遅延構文）

```julia
# Aは行列で、bは応答ベクトルです。 
sol = @> setupRegularizationProblem(A, 1) solve(b)
```
