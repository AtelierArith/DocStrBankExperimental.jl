```
factor_shift(IA::IntermediateAlmostBlockDiagonal, ipivot::AbstractArray{I}, scrtch)
```

Factorize the intermediate representation of almost block diagonals matrix `IA[i]` and then shift to prepare the next block `IA[i+1]`.
