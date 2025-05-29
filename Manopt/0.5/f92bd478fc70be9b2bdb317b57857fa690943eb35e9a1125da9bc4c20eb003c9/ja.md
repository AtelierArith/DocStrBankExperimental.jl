```
ManifoldStochasticGradientObjective{T<:AbstractEvaluationType} <: AbstractManifoldGradientObjective{T}
```

確率的勾配目的関数は以下で構成されます。

  * （オプションの）コスト関数 $f(p) = \displaystyle\sum_{i=1}^n f_i(p)$
  * 勾配の配列、$\operatorname{grad}f_i(p), i=1,\ldots,n$ は二つの形式で提供できます。

      * 一つの関数として $(\mathcal M, p) ↦ (X_1,…,X_n) ∈ (T_p\mathcal M)^n$
      * 関数のベクトルとして $\bigl( (\mathcal M, p) ↦ X_1, …, (\mathcal M, p) ↦ X_n\bigr)$。

どちらの形式も [`InplaceEvaluation`](@ref) 関数 `(M, X, p) -> X` として提供でき、ここで `X` は `X1,...,Xn` のベクトルであり、`(M, X1, p) -> X1, ..., (M, Xn, p) -> Xn` となります。

# コンストラクタ

```
ManifoldStochasticGradientObjective(
    grad_f::Function;
    cost=Missing(),
    evaluation=AllocatingEvaluation()
)
ManifoldStochasticGradientObjective(
    grad_f::AbstractVector{<:Function};
    cost=Missing(), evaluation=AllocatingEvaluation()
)
```

勾配を一つの関数（接ベクトルの配列を返す）または関数のベクトル（それぞれが一つの接ベクトルを返す）として持つ確率的勾配問題を作成します。

オプションのコストは、単一の関数（数値を返す）または値を返す関数のベクトルとしても提供できます。

# 使用例

[`stochastic_gradient_descent`](@ref)

これは [`gradient_descent`](@ref) とも使用できることに注意してください。なぜなら、（完全な）勾配は単一の勾配の合計に過ぎないからです。
