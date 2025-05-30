```
convective_derivative!(out,q)
```

`q`の対流微分を$u\cdot\nabla u$の形で計算し、その結果を`out`に格納します。結果は任意のグリッド間隔でスケーリングされていないことに注意してください。
