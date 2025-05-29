```
number_field(f::NumFieldEmb) -> NumField
```

埋め込み $f$ の対応する数体を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K)[1];

julia> number_field(e)
虚数二次体は x^2 + 3 によって定義されます
```
