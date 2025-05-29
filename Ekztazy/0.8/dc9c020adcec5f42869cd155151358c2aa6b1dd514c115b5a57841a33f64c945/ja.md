```
fetchval(f::Future{Response{T}}) -> Nullable{T}
```

`fetch(f).val` のショートカット: [`Response`](@ref) を取得し、その値を返します。レスポンスの成功や返される値に関する保証はなく、HTTPレスポンスやキャッチされた例外など、デバッグに役立つコンテキストが破棄されることに注意してください。
