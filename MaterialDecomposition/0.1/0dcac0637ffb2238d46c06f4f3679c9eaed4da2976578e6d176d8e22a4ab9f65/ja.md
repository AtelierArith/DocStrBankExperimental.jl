```
fit_calibration(calculated_calcium_intensities, calcium_densities, p0::AbstractVector=zeros(8))
```

キャリブレーション方程式で、`p0`は基礎データにフィットさせる必要がある初期パラメータのベクトルです（`calculated_calcium_intensities`）、これはさまざまなカルシウムキャリブレーションロッドの密度に対する「高」および「低」エネルギー測定値を含んでいます（`known_calcium_densities`）。`LsqFit.curve_fit`は、キャリブレーションされたパラメータ`p`を返します。

注: `calculated_calcium_intensities`は、`n x 2`配列の最初の列に「低エネルギー」強度計算を、`n x 2`配列の2番目の列に「高エネルギー」強度計算を含むことが期待されています。
