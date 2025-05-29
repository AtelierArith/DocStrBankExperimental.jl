```
ConstantLength(s; kwargs...)
ConstantLength(M::AbstractManifold, s; kwargs...)
```

定数の[`Stepsize`](@ref)を指定します。

# 入力

  * `M`（オプション）

`s=min( injectivity_radius(M)/2, 1.0)` : 使用する長さ。

# キーワード引数

  * `type::Symbol=relative` 定数ステップサイズのタイプを指定します。

      * `:relative` – 勾配接ベクトル $X$ を $s*X$ にスケールします
      * `:absolute` – 勾配を絶対ステップ長 $s$ にスケールします。すなわち、$\frac{s}{\lVert X \rVert_{}}X$

!!! info
    この関数は[`ConstantStepsize`](@ref)のための[`ManifoldDefaultsFactory`](@ref)を生成します。多様体に依存するデフォルト値について、このファクトリーは、例えば対応する[`AbstractManoptSolverState`](@ref)から多様体が利用可能になるまで構築を延期します。

