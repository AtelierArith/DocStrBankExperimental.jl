```
interpolate(c0:: Curve, c1:: Curve; kwargs...):: Curve
```

Curve ˋc0ˋ の x 軸のポイントで Curve ˋc1ˋ を補間し、補間されたポイント上に新しい Curve インスタンスを返します。

出力される Curve はデフォルト設定を使用して構築され、代替設定は ˋkwargs...ˋ を使用して Curve コンストラクタに渡すことができます。
