```
get_vectors(M::AbstractManifold, p, B::AbstractBasis=get_basis(M, p, DefaultOrthonormalBasis()))
```

点 `p` における接空間の基底 `B` の基底ベクトルを取得します。 [`CachedBasis`](@ref) 以外の基底が渡された場合、関数は動作する場合としない場合があります。 `CachedBasis` は [`get_basis`](@ref) を呼び出すことで取得できます。
