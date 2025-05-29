```
DegreasingLength(; kwargs...)
DecreasingLength(M::AbstractManifold; kwargs...)
```

指定された [`Stepsize`] は次のように減少します ``s_k = \frac{(l - ak)f^i}{(k+s)^e} で、以下の

# キーワード引数

  * `exponent=1.0`:   分母の指数 $e$
  * `factor=1.0`:     分子の係数 $f$
  * `length=min(injectivity_radius(M)/2, 1.0)`: 初期ステップサイズ $l$。
  * `subtrahend=0.0`: 各イテレーションで引かれる値 $a$
  * `shift=0.0`:      分母のイテレーター $k$ を $s$ だけシフトします。
  * `type::Symbol=relative` 定数ステップサイズのタイプを指定します。
  * `:relative` – 勾配接線ベクトル $X$ を $s_k*X$ にスケールします
  * `:absolute` – 勾配を絶対ステップ長 $s_k$ にスケールします。すなわち $\frac{s_k}{\lVert X \rVert_{}}X$

!!! info
    この関数は [`DecreasingStepsize`](@ref) のための [`ManifoldDefaultsFactory`](@ref) を生成します。多様体に依存するデフォルト値については、このファクトリーは、例えば対応する [`AbstractManoptSolverState`](@ref) から多様体が利用可能になるまで構築を延期します。

