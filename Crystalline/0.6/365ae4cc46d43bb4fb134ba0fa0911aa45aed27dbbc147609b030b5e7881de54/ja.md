```julia
wyckoffs(
    sgnum::Integer
) -> Vector{Crystalline.WyckoffPosition{3}}
wyckoffs(sgnum::Integer, ::Val{D}) -> Any

```

空間群 `sgnum` のワイコフ位置を次元 `D` として `Vector{WyckoffPosition{D}` で返します。

位置は、ビルバオ結晶学サーバーの規則に従って、従来の基底設定で与えられます（基になるデータはここから取得されます [^1]）。

## 例

```jldoctest
julia> wps = wyckoffs(16, 2)
4-element Vector{WyckoffPosition{2}}:
 6d: [α, β]
 3c: [1/2, 0]
 2b: [1/3, 2/3]
 1a: [0, 0]
```

## 参考文献

[^1]: Aroyo, *et al.*,   [Z. Kristallogr. **221**, 15-27 (2006)](https://doi.org/0.1524/zkri.2006.221.1.15)
