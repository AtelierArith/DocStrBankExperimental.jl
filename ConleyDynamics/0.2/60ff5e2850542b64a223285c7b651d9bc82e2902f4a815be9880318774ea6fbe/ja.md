```
morse_sets(lc::LefschetzComplex, mvf::CellSubsets; poset::Bool=false)
```

Lefschetz複体上の多ベクトル場の非自明なモース集合を見つけます。

入力引数 `lc` にはLefschetz複体が含まれ、`mvf` は多ベクトル場を説明します。この関数は非自明なモース集合を `Vector{Vector{Int}}` として返します。オプション引数 `poset=true` を追加すると、関数はモース集合と基礎となる部分順序集合のハッセ図の隣接行列の両方を返します。
