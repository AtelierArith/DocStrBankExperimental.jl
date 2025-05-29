```
GradientDescentState{P,T} <: AbstractGradientSolverState
```

勾配に基づく降下アルゴリズムを説明します。

# フィールド

初期化時にパラメータを省略できる場合、デフォルト値が括弧内に示されています。

  * `p`:                  （`rand(M)` 現在の反復点
  * `X`:                  （`zero_vector(M,p)`）現在の勾配 $\operatorname{grad}f(p)$、初期値はゼロベクトルです。
  * `stopping_criterion`: （[`StopAfterIteration`](@ref)`(100)`) [`StoppingCriterion`](@ref)
  * `stepsize`:           （[`default_stepsize`](@ref)`(M, GradientDescentState)`) [`Stepsize`](@ref)
  * `direction`:          （[`IdentityUpdateRule`](@ref)）勾配を計算するためのプロセッサ
  * `retraction_method`:  （`default_retraction_method(M, typeof(p))`）使用するリトラクション、マニフォールドのデフォルト設定に従います。

# コンストラクタ

```
GradientDescentState(M, p=rand(M); X=zero_vector(M, p), kwargs...)
```

勾配降下オプションを生成します。ここで、`X`は特定のタイプで勾配を格納する接ベクトルを設定するために使用できます。他のすべてのフィールドはキーワード引数です。

# 参照

[`gradient_descent`](@ref) ```
