```
PreconditionedDirection(preconditioner; kwargs...)
PreconditionedDirection(M::AbstractManifold, preconditioner; kwargs...)
```

勾配プロセッサに前処理器を追加します。これは、最適化の[動機](https://en.wikipedia.org/wiki/Preconditioner#Preconditioning_in_optimization)に従い、通常は線形可逆写像 $P: T_{p}\mathcal M → T_{p}\mathcal M$ であるべきです。

  * 対称性: $⟨X, P(Y)⟩ = ⟨P(X), Y⟩$
  * 正定値性: $⟨X, P(X)⟩ > 0$ ただし $X$ はゼロベクトルでない

勾配は $P(X)$ として前処理され、ここで $X$ は目的関数の勾配または以前の（内部に保存された）勾配プロセッサの結果です。

例えば、前処理器としてヘッセ行列の逆 $\operatorname{Hess}^{-1} f$ を提供すると、勾配降下法をニュートン法に変換します。

# 引数

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$ （オプション）
  * `preconditioner`:   前処理器関数、`(M, p, X) -> Y` のような割り当て関数または `(M, Y, p, X) -> Y` のような変更関数

# キーワード引数

  * `direction=`[`IdentityUpdateRule`](@ref) 内部 [`DirectionUpdateRule`](@ref) 勾配を保存するかどうかを決定するか、またはそれを生成する [`ManifoldDefaultsFactory`](@ref)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を変更してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であるため、変更された引数は2番目になります。

!!! info
    この関数は [`PreconditionedDirectionRule`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値について、このファクトリーは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。


```
