```
permutedims!(dest, src, perm)
```

配列 `src` の次元を置換し、その結果を配列 `dest` に格納します。`perm` は `ndims(src)` の長さを持つ置換を指定するベクターです。事前に割り当てられた配列 `dest` は `size(dest) == size(src)[perm]` である必要があり、完全に上書きされます。インプレースの置換はサポートされておらず、`src` と `dest` が重複するメモリ領域を持つ場合、予期しない結果が生じる可能性があります。

詳細は [`permutedims`](@ref) を参照してください。
