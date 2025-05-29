```
de2f2poly(d::Integer; width::Int = 0)::Polynomial{F2,:x}
```

10進数をF2上の多項式に変換します。

# 引数

  * `d::Integer`: 変換する10進数
  * `width::Int = 0`: 多項式係数の希望する幅。0の場合、必要な最小幅が使用されます。

# 戻り値

  * `Polynomial{F2,:x}`: 入力数の2進数形式を表すF2上の多項式

# 例

```julia
julia> de2f2poly(5)
Polynomial(1 + x^2)

julia> de2f2poly(5, width=4)
Polynomial(1 + x^2)
```
