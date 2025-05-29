この関数は、特定のトレースが特定の帯域幅で費やす時間の量です。私は、これはペッパーバーグに似ていると思います。したがって、これはその関数になるかもしれません。「基準」はパーセントです。この関数は、応答が特定の基準量 (iᵣ) に戻るのにかかる時間を測定します。-デフォルトでは、iᵣは0.60に設定されています。

```
初期の問題は、関数がドリフトや他のパケットを拾う傾向があることです。非連続パケットを排除することができます。
この関数の詳細については、次を参照してください。
    Pepperburg & Cornwall et al. Light-dependent delay in the falling phase of the retinal rod photoresponse

使用法:
>>> rmaxes = saturated_response(data1_testA)
>>> Tᵣ = percent_recovery_interval(data1_testA, rmaxes)
```
