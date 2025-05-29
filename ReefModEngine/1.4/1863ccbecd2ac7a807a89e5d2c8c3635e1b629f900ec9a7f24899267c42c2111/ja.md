非エラーの数値結果がRME関数から返される場合のみ使用します。

# 例

```julia
count_per_m2::Float64 = @getRME ivOutplantCountPerM2("iv_name"::Cstring)::Cdouble
```
