```julia
InterpolatedModel(model, grid; algorithm)

```

モデルのフーリエ領域での表現を補間とFFTを使用して計算します。これは、フーリエ領域で直接表現できないモデルを構築するのに役立ちます。

# 注意

これは主にテストおよびデバッグの目的で使用されます。一般的には、人々はモデルのフーリエ変換を計算するために[`FourierDualDomain`](@ref)機能を使用すべきです。
