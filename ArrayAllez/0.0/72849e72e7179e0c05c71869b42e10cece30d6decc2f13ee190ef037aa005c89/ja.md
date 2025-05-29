```
similar_(name, A)     ≈ similar(A)
Array_{T}(name, size) ≈ Array{T}(undef, size)
```

中間結果の新しい配列は、`length(A) >= 2000` の場合にLRUキャッシュから取得されます。キャッシュのキーは、異なる使用が衝突しないように `name::Symbol` と型およびサイズを使用します。

```
copy_(name, A) = copyto!(similar_(name, A), A)
```

そのように。
