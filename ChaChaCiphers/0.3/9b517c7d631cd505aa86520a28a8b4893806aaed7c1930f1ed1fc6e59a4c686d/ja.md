```
encrypt(stream::ChaChaStream, x)
encrypt!(stream::ChaChaStream, x)
```

[`ChaChaStream`](@ref)からのキーストリームを使用して、ベクトルまたは文字列`x`を暗号化します。
