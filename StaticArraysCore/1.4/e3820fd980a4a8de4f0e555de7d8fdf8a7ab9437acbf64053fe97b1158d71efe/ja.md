```
SizedArray{Tuple{dims...}}(array)
```

静的サイズを持つ `AbstractArray` をラップし、StaticArrays.jl によって定義された（より高速な）メソッドを活用できるようにします。サイズは構築時に一度チェックされ、要素数（`length`）が一致するかどうかが確認されますが、配列は再形成可能です。

エイリアス `SizedVector{N}` と `SizedMatrix{N,M}` は、1次元および2次元の `SizedArray` のより便利な名前として提供されています。たとえば、2x3 の配列 `a` を `SizedArray` でラップするには、`SizedMatrix{2,3}(a)` を使用します。
