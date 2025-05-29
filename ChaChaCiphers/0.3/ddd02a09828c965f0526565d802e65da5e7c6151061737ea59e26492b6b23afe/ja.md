```
decrypt(stream::ChaChaStream, x)
decrypt!(stream::ChaChaStream, x)
```

暗号化されたベクトル `x` を [`ChaChaStream`](@ref) からのキーストリームを使用して復号化します。
