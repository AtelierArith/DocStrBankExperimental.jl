```
mb03wd!(job::AbstractChar, compz::AbstractChar, n::Integer, p::Integer, 
        ilo::Integer, ihi::Integer, iloz::Integer, ihiz::Integer,  h::Array{Float64, 3}, z::Array{Float64, 3}, 
        wr::AbstractVector{Float64}, wi::AbstractVector{Float64}, ldwork::Integer) -> info::Int64
```

行列の積 H = `H_1`*`H_2`*...*`H_p` のシュア分解と固有値を計算します。ここで、`H_1` は上部ヘッセンベルグ行列であり、`H_2`, ..., `H_p` は上三角行列です。積を評価することなく、行列 `Z_i` を計算します。具体的には、

```
    `Z_1' * H_1 * Z_2 = T_1,`
    `Z_2' * H_2 * Z_3 = T_2,`
           `...`
    `Z_p' * H_p * Z_1 = T_p,`
```

ここで `T_1` は実シュア形式であり、`T_2`, ..., `T_p` は上三角です。

このルーチンは主に行列 H*i の行と列 ILO から IHI のヘッセンベルグおよび三角部分行列で動作しますが、オプションで行列 H*i のすべての行と列に変換を適用することもできます。変換はオプションで累積することができます。

詳細については、`MB03WD` の SLICOT ドキュメントを参照してください。
