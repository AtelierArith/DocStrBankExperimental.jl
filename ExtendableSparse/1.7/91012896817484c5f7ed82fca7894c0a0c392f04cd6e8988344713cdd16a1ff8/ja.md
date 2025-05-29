```
    LinearSolvePreconBuilder(; method=UMFPACKFactorization())
```

呼び出し可能なオブジェクトを返し、`precs` パラメータとして LinearSolve を使用してスパース LU 因子分解から形式的な左前処理器を構築します。これは [`BlockPreconBuilder`](@ref) または LinearSolve.jl によってラップされた反復法に使用されます。
