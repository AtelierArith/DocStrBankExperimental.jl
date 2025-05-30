```
which(f, types)
```

指定された `types` の引数に対して呼び出される `f` のメソッド（`Method` オブジェクト）を返します。

`types` が抽象型である場合、`invoke` によって呼び出されるメソッドが返されます。

関連情報: [`parentmodule`](@ref)、および [`InteractiveUtils`](@ref man-interactive-utils) の `@which` と `@edit`。
