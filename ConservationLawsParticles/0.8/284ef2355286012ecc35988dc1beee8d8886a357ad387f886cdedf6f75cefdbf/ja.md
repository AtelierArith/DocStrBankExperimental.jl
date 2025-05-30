```
pwc_densities!(dens, xs::AbstractVector{<:Real}...)
pwc_densities!(dens, xs::Tuple{Vararg{AbstractVector{<:Real}}})
```

これは、結果を `dens` に書き込む [`pwc_densities`](@ref) のインプレースバージョンです。

説明については、[`pwc_densities`](@ref) のドキュメントを参照してください。
