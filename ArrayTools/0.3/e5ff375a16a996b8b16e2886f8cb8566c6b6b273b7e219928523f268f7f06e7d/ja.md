```
to_fast_array([T=eltype(A),] A)
```

遅延的に `A` と同等の *fast array* を要素型 `T` で生成します。*fast array* は標準の1ベースインデックスを持ち、線形インデックスによって効率的にインデックス付けされます。もし `A` がすでに要素型 `T` の *fast array* であれば、`A` が返されます。そうでない場合、`A` は `Array` に変換されて返されます。

他にも [`is_fast_array`](@ref)、[`IndexingType`](@ref)、[`to_flat_array`](@ref) を参照してください。
