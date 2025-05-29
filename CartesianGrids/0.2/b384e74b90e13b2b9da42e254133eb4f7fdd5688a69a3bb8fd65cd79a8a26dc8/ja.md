```
convective_derivative_rot!(out,q)
```

`q`の対流微分の回転形式を$\frac{1}{2}\nabla|u|^2-u\times(\nabla\times u)$の形で計算し、その結果を`out`に格納します。結果は任意のグリッド間隔でスケーリングされていないことに注意してください。
