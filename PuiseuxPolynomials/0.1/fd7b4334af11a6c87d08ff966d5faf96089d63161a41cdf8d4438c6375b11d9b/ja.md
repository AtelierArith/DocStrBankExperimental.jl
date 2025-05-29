`grobner_basis(F;lt=lex)`

は、ベクトル `F` によって与えられる `Mvp` によって生成される多項式イデアルのグレブナー基底を計算します。キーワード `lt` は使用する単項式順序を説明します。

```julia-repl
julia> @Mvp x,y,z; F=[x^2+y^2+z^2-1,x^2-y+z^2,x-z]
3-element Vector{Mvp{Int64, Int64}}:
 x²+y²+z²-1
 x²-y+z²
 x-z

julia> grobner_basis(F)
3-element Vector{Mvp{Rational{Int64}, Int64}}:
 (1//1)x+(-1//1)z
 (-1//1)y+(2//1)z²
 (4//1)z⁴+(2//1)z²-1//1

julia> grobner_basis(F;lt=grlex)
3-element Vector{Mvp{Rational{Int64}, Int64}}:
 (1//1)x+(-1//1)z
 (1//1)y²+(1//1)y-1//1
 (-1//1)y+(2//1)z²

julia> grobner_basis(F;lt=grevlex)
3-element Vector{Mvp{Rational{Int64}, Int64}}:
 (1//1)x+(-1//1)z
 (1//1)y²+(1//1)y-1//1
 (2//1)x²+(-1//1)y
```

変数の順序を変更するためのキーワードはありません。この目的のために `rename_variables` を使用することをお勧めします。
