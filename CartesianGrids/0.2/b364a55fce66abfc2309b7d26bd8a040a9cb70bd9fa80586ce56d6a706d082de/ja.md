```
directional_derivative!(out,f,q)
```

関数 `f` の方向導関数を方向 `q` に沿って計算し、$q\cdot\nabla f$ の結果を `out` に格納します。結果はグリッド間隔でスケーリングされていないことに注意してください。
