```
standard_size(A) -> size(A)
```

は `A` の次元のリスト、すなわち `size(A)` を返します。`A` が標準の1ベースのインデックスを持っていない場合は、`ArgmentError` 例外をスローします。

また、[`has_standard_indexing`](@ref) や [`same_standard_size`](@ref) も参照してください。
