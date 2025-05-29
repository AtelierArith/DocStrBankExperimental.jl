```
sketch([F=hash], it, s::Integer)
```

イテラブル `it` の各要素を関数 `F` を使ってハッシュ化し、最大で `s` 個の最小ハッシュを含む `MinHashSketch` を返します。

# 例:

```jldoctest
julia> sketch("ACGDEFG", 3)
MinHashSketch:
 hashes:  3 / 3
 maxhash: 0x3e1b023d3c92ff8f
```

関連情報: [`update!`](@ref) ```
