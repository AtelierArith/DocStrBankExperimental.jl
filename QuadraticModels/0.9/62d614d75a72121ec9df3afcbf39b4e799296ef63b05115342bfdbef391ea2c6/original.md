```
qp = QuadraticModel(c, Hrows, Hcols, Hvals; Arows = Arows, Acols = Acols, Avals = Avals, 
                    lcon = lcon, ucon = ucon, lvar = lvar, uvar = uvar, sortcols = false)

qp = QuadraticModel(c, H; A = A, lcon = lcon, ucon = ucon, lvar = lvar, uvar = uvar)
```

Create a Quadratic model $min ~\tfrac{1}{2} x^T H x + c^T x + c_0$ with optional bounds `lvar ≦ x ≦ uvar` and optional linear constraints `lcon ≦ Ax ≦ ucon`. The user should only give the lower triangle of `H` to the `QuadraticModel` constructor.

With the first constructor, if `sortcols = true`, then `Hcols` and `Acols` are sorted in ascending order  (`Hrows`, `Hvals` and `Arows`, `Avals` are then sorted accordingly).

You can also use [`QPSReader.jl`](https://github.com/JuliaSmoothOptimizers/QPSReader.jl) to create a Quadratic model from a QPS file:

```
using QPSReader
qps = readqps("QAFIRO.SIF")
qp = QuadraticModel(qps)
```

The instance of `QuadraticModel{T, S, D}` created contains the fields:

  * `meta` of type [`NLPModels.NLPModelMeta`](https://juliasmoothoptimizers.github.io/NLPModels.jl/stable/models/#NLPModels.NLPModelMeta)  from [`NLPModels.jl`](https://github.com/JuliaSmoothOptimizers/NLPModels.jl),
  * `data`, of type `QuadraticModels.QPData` depending on the input types of the `A` and `H` matrices.
  * `counters` of type [`NLPModels.Counters`](https://juliasmoothoptimizers.github.io/NLPModels.jl/stable/reference/#NLPModels.Counters) from [`NLPModels.jl`](https://github.com/JuliaSmoothOptimizers/NLPModels.jl).

Using [`NLPModelsModifiers.SlackModel`](https://juliasmoothoptimizers.github.io/NLPModelsModifiers.jl/stable/reference/#NLPModelsModifiers.SlackModel) from [`NLPModelsModifiers.jl`](https://github.com/JuliaSmoothOptimizers/NLPModelsModifiers.jl) with a `QuadraticModel`  based on a `QPData` with dense matrices will convert the field `data` to a `QPData` with SparseMatricesCOO.  

Its in-place variant `SlackModel!` specific to QuadraticModels will only work with a `QuadraticModel` based on a `QPData` with SparseMatricesCOO.
