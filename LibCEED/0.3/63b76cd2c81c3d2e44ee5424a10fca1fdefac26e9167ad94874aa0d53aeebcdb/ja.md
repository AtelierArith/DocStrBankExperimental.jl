```
norm(v::CeedVector, ntype::NormType)
```

与えられた [`CeedVector`](@ref) のノルムを返します。

ノルムのタイプは `NORM_1`、`NORM_2`、`NORM_MAX` のいずれかとして指定できます。
