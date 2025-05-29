```
EmbeddedVectorTransport{T<:AbstractVectorTransportMethod} <: AbstractVectorTransportMethod
```

埋め込みでのベクトル輸送のタイプ `T` を使用してベクトル輸送を計算し、結果を投影します。

# コンストラクタ

```
EmbeddedVectorTransport(vt::AbstractVectorTransportMethod)
```

埋め込みで使用するベクトル輸送 `vt` を持つベクトル輸送を生成します。
