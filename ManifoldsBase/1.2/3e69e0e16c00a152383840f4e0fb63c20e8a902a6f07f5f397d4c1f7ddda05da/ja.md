```
allocate(a)
allocate(a, dims::Integer...)
allocate(a, dims::Tuple)
allocate(a, T::Type)
allocate(a, T::Type, dims::Integer...)
allocate(a, T::Type, dims::Tuple)
allocate(M::AbstractManifold, a)
allocate(M::AbstractManifold, a, dims::Integer...)
allocate(M::AbstractManifold, a, dims::Tuple)
allocate(M::AbstractManifold, a, T::Type)
allocate(M::AbstractManifold, a, T::Type, dims::Integer...)
allocate(M::AbstractManifold, a, T::Type, dims::Tuple)
```

オブジェクト `a` に似たものを割り当てます。これは関数 `similar` に似ていますが、ネストされた構造の最外層だけでなく、外層を再帰的にマッピングし、最も内側の配列のようなオブジェクトに対してのみ `similar` を呼び出します。型 `T` は新しい数値要素の型 [`number_eltype`](@ref) であり、指定されていない場合は `a` の要素型が保持されます。`dims` 引数は非ネストされた割り当てのために与えることができ、関数 `similar` に転送されます。

その動作は特定の多様体によってオーバーライドされることがあります。たとえば、ネストされた置換表現を持つ冪多様体は、`Array{<:SArray}` に対する `allocate` がデフォルトで行われるように `Array{<:MArray}` ではなく別の `Array{<:SArray}` を返すことを決定できます。
