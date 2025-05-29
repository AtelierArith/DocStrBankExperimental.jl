```
norm(v::CeedVector, p::Real)
```

与えられた [`CeedVector`](@ref) のノルムを返します。詳細は [`norm(::CeedVector, ::NormType)`](@ref) を参照してください。

`p` は 1、2、または Inf の値を持つことができ、それぞれ `NORM_1`、`NORM_2`、および `NORM_MAX` に対応します。
