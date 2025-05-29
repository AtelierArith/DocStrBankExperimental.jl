```
KrylovLinearSolver
```

線形システム `Ax = b` および `AX = B` を組み込みの `\` と同様に解くことができる呼び出し可能なオブジェクトです。内部では [Krylov.jl](https://github.com/JuliaSmoothOptimizers/Krylov.jl) の反復ソルバーを使用します。

# コンストラクタ

```
KrylovLinearSolver(; verbose=true)
```

`verbose` が `true` の場合、ソルバーは失敗時に警告をログに記録します。そうでない場合は静かに失敗し、線形システムを正確に満たさない解を返す可能性があります。

# 呼び出し可能な動作

```
(::KylovLinearSolver)(A, b::AbstractVector)
```

単一の右辺を持つ線形システムを解きます。

```
(::KrylovLinearSolver)(A, B::AbstractMatrix)
```

複数の右辺を持つ線形システムを解きます。
