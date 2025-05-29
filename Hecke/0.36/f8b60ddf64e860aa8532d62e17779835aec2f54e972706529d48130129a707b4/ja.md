```
coxeter_number(ADE::Symbol, n) -> Int
```

対応するADEルート格子のコクセター数を返します。

もし$L$がルート格子であり、$R$がそのルートの集合であるなら、コクセター数$h$は$|R|/n$であり、ここで`n`は$L$の階数です。

# 例

```jldoctest
julia> coxeter_number(:D, 4)
6

```
