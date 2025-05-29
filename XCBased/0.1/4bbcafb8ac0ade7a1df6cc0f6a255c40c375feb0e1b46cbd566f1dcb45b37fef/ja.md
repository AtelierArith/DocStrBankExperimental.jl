```
XCBVoidFuture <: XCBFuture
```

応答を生成しないリクエストは `XCBVoidFuture` を返します。この未来タイプが [`fetch`](@ref) されると、`fetch` は `nothing` を返します。したがって、この未来タイプに対しては `fetch` と [`wait`](@ref) の間に違いはありません。
