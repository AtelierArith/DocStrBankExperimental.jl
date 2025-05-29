```julia
solve(
    prob::Union{HighDimPDE.PIDEProblem, HighDimPDE.ParabolicPDEProblem},
    alg::HighDimPDE.MLP;
    multithreading,
    verbose
) -> HighDimPDE.PIDESolution{_A, _B, Nothing, _C, Nothing, Nothing} where {_A, _B, _C}

```

`PIDESolution`オブジェクトを返します。

# 引数

  * `multithreading` : `true`の場合、利用可能なすべてのスレッドに仕事を分配します。
  * `verbose`: イテレーションに関する情報を印刷します。
