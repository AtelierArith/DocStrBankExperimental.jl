```
SmallCollections
```

このパッケージは、固定または制限された（小さな）数の要素を保持できる可変および不変のコレクションをいくつか提供し、例えば `Set` や `Vector` よりもはるかに効率的です。これは特に不変のバリアントに当てはまり、要素型が `isbitstype` を満たす場合、メモリを割り当てません。現在、`FixedVector`、`SmallVector`、`SmallDict`、`SmallSet` およびそれらの可変対応物、さらに `PackedVector` と `SmallBitSet` が定義されています。

サブモジュール [`Combinatorics`](@ref) には、列挙的組合せ論に関連する関数が含まれています。

パッケージ `BangBang.jl` がロードされている場合、このパッケージによって定義された多くの関数は `!!` 形式でも利用可能です。例えば、`SmallVector` を最初の引数として `setindex!!` を呼び出すと、[`setindex`](@ref) が呼び出されます。

このパッケージで定義された関数の境界チェックは、`@inbounds` マクロを使用することでスキップできます。

[`AbstractFixedVector`](@ref)、[`AbstractSmallDict`](@ref)、[`AbstractSmallSet`](@ref)、[`AbstractSmallVector`](@ref)、[`PackedVector`](@ref)、[`SmallBitSet`](@ref)、[`Combinatorics`](@ref)、`Base.@inbounds`、`Base.isbitstype`、[セクション "BangBang サポート"](@ref sec-bangbang) を参照してください。
