```
bcastcopy(A, [T=eltype(A),] dims...)
```

は、型変換とブロードキャストルール（`broadcast` メソッドの場合と同様）に従って、`A` によって与えられる値を持つ要素型 `T` と次元 `dims` の新しい配列を生成します。 [`bcastlazy`](@ref) と比較して、返される配列は `A` と内容を共有しないことが保証されています。

引数 `A` はスカラー値または配列であることができます。

他にも [`bcastlazy`](@ref)、[`bcastsize`](@ref) を参照してください。
