```
find_spans(func, x, p)

関数が符号を変える範囲を見つけます。

# 引数
- `func::Function`: 範囲を見つけるための関数。
- `x::Vector{Real}`: x 値。
- `p::Vector{Real}`: パラメータ。

# 戻り値
- `Vector{eltype(x)}`: 範囲。
```
