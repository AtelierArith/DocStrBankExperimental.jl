```
HybridArray{Tuple{dims...}}(array)
```

静的および動的サイズの組み合わせを持つ `AbstractArray` をラップし、StaticArrays パッケージによって定義された（より高速な）メソッドを活用できるようにします。サイズは構築時に一度チェックされ、要素の数（`length`）が一致するかどうかを判断しますが、配列は再形成される可能性があります。
