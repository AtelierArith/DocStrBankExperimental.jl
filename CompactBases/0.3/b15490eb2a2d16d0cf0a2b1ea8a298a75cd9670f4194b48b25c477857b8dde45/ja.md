```
basis_overlap(A::BSplineOrRestricted, B::Union{BSplineOrRestricted,FEDVROrRestricted})
```

区分多項式基底、すなわちBスプラインまたはFEDVRから、ガウス求積法を使用して重なり行列要素を正確に計算できます。FEDVR基底関数がガウス–ロバット求積法の意味で直交しているという事実を利用すれば、より良い結果を導出できる可能性がありますが、それについては後で考えます。
