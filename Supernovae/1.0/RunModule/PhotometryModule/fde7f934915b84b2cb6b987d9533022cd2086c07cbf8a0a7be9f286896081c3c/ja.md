```
flux_to_mag(flux::Unitful.Quantity{Float64}, zeropoint::Level)
```

フラックスをマグニチュードに変換します。`zeropoint - 2.5log10(flux)`を計算します。`AB_mag`単位を返します。

# 引数

  * `flux::Unitful.Quantity{Float64}`: Janskyと互換性のある単位で変換するフラックス。フラックスが負の場合は、`log10`エラーを避けるために0.0に設定されます。
  * `zeropoint::Level`: フラックスをマグニチュードに変換するために使用される仮定されたゼロポイント。
