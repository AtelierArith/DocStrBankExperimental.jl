```
nb_fp_numbers(a::Floatmu{szE,szf}, b::Floatmu{szE,szf}) where {szE,szf}
```

区間 $[a,b]$ に含まれる浮動小数点数の数を返します。もし $a > b$ の場合は、`ArgumentError` 例外をスローします。

# 例

```jldoctest
julia> nb_fp_numbers(Floatmu{2, 2}(-0.0),Floatmu{2, 2}(0.0))
1
julia> nb_fp_numbers(Floatmu{2, 2}(3.0),Floatmu{2, 2}(3.5))
2
```
