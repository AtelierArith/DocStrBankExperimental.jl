```
directional_derivative_conserve!(out,f,q)
```

関数 `f` の方向 `q` における保守的な方向微分の形 $\nabla\cdot(qf)$ を計算し、その結果を `out` に格納します。結果はグリッド間隔でスケーリングされていないことに注意してください。この形は `q` が発散しない場合にのみ適切です。
