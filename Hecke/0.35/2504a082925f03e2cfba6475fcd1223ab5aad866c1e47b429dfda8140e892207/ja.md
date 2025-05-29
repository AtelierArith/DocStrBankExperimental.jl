```
is_imaginary(f::NumFieldEmb) -> Bool
```

埋め込みが虚数である場合、すなわち実数でない場合に `true` を返します。

# 例

```jldoctest
julia> K, a = quadratic_field(-3); e = complex_embeddings(K)[1];

julia> is_imaginary(e)
true
```
