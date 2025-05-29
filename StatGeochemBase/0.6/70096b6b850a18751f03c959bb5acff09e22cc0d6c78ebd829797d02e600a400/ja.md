```julia
parsedlm(str::AbstractString, delimiter::Char, T::Type=Float64; rowdelimiter::Char='\n', merge::Bool=false)
```

行と列で区切られた文字列を単一の（2-D）行列に解析します。デフォルトの列区切り文字は改行です。ファイルではなく文字列で動作する`readdlm`に似ています。

### 例

```julia
julia> parsedlm("1,2,3
4,5,6
7,8,9
", ',', Float64)
3×3 Matrix{Float64}:
 1.0  2.0  3.0
 4.0  5.0  6.0
 7.0  8.0  9.0

julia> parsedlm("1,2,3,4
5,6,7,8
9,10,11,12
13,14,15,16", ',', Int64)
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16
```
