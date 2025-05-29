```
blockdim(P::ProductSpace, c::Sector)
```

結合されたセクター `c` の総次元を、`c` に融合できるすべてのセクターのタプル `s::NTuple{N, <:Sector}` に対して `dim(P, s)` を合計することによって返します。これは、`s` が `c` に融合できる方法の数（すなわち、正しい重複度で数えられた方法の数）でカウントされます。

[`hasblock`](@ref) および [`blocksectors`](@ref) も参照してください。
