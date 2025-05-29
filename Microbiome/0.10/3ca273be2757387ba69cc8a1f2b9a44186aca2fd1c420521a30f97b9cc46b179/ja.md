```
Taxon(name::String, rank::Union{Missing, Symbol, Int}) <: AbstractFeature
Taxon(name::String)
```

名前とランクを持つ微生物の分類群で、ランクは次のいずれかです。

0. `:domain`
1. `:kingom`
2. `:phylum`
3. `:class`
4. `:order`
5. `:faamily`
6. `:genus`
7. `:species`
8. `:subspecies`
9. `:strain`

または `missing`。コンストラクタは0-9の数字を使用することも、文字列のみを渡すこともできます（この場合、`taxon`は`missing`として保存されます）。

詳細は [`taxon`](@ref Microbiome.taxon) を参照してください。
