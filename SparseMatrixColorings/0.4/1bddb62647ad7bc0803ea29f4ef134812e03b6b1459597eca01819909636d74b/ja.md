```
fast_coloring(
    S::AbstractMatrix,
    problem::ColoringProblem,
    algo::GreedyColoringAlgorithm;
    [symmetric_pattern=false]
)
```

行列 `S` に対して [`ColoringProblem`](@ref) を [`GreedyColoringAlgorithm`](@ref) で解決し、次のものを返します。

  * `:column` および `:row` 問題に対しては単一の色ベクトル
  * `:bidirectional` 問題に対しては色ベクトルのタプル

この関数は [`coloring`](@ref) と非常に似ていますが、計算をスキップして [`AbstractColoringResult`](@ref) を計算しないことで速度を向上させています。

# 参照

  * [`coloring`](@ref)
