```
macrorecall(goldI::AbstractMatrix, resI::AbstractMatrix, k=size(goldI, 1))::Float64
```

Computes the macro recall score using goldI as gold standard and resI as predictions; it expects that matrices of integers (identifiers). If `k` is given, then the results are cut to first `k`.
