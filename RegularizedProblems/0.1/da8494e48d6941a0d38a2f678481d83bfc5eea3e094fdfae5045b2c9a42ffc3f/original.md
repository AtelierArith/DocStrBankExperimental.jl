```
model, nls_model, sol = bpdn_model(args...; kwargs...)
model, nls_model, sol = bpdn_model(compound = 1, args...; kwargs...)
```

Return an instance of an `NLPModel` and an instance of an `NLSModel` representing the same basis-pursuit denoise problem, i.e., the under-determined linear least-squares objective

½ ‖Ax - b‖₂²,

where A has orthonormal rows and b = A * x̄ + ϵ, x̄ is sparse and ϵ is a noise vector following a normal distribution with mean zero and standard deviation σ.

## Arguments

  * `m :: Int`: the number of rows of A
  * `n :: Int`: the number of columns of A (with `n` ≥ `m`)
  * `k :: Int`: the number of nonzero elements in x̄
  * `noise :: Float64`: noise standard deviation σ (default: 0.01).

The second form calls the first form with arguments

```
m = 200 * compound
n = 512 * compound
k =  10 * compound
```

## Keyword arguments

  * `bounds :: Bool`: whether or not to include nonnegativity bounds in the model (default: false).

## Return Value

An instance of a `FirstOrderModel` and of a `FirstOrderNLSModel` that represent the same basis-pursuit denoise problem, and the exact solution x̄.

If `bounds == true`, the positive part of x̄ is returned.
