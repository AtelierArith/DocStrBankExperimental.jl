```
interpolate(xval:: AbstractArray{T} where T, c1:: Curve; kwargs...):: Curve
```

与えられた配列に曲線を補間し、補間された点に基づいて新しいCurveインスタンスを返します。

出力されるCurveはデフォルト設定を使用して構築され、代替設定はCurveコンストラクタにˋkwargs...ˋを使用して渡すことができます。
