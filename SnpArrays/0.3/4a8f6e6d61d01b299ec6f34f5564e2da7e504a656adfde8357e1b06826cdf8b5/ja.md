```
grm(s, method=:GRM, minmaf=0.01, colinds=nothing)
```

SnpArray `s` から経験的親族行列を計算します。欠損遺伝子型は列の平均でその場で補完されます。

# 引数

  * `method::Symbol=:GRM`: `:GRM`（デフォルト）、`:MoM`、または `:Robust`。
  * `minmaf::Real=0.01`: MAF が `minmaf` より小さい列は除外されます；デフォルトは 0.01。
  * `cinds=nothing`: GRM を計算するために使用される列のインデックスまたはマスク。
  * `t::Type{T}=Float64`: GRM を計算するための浮動小数点型；デフォルトは `Float64`。
