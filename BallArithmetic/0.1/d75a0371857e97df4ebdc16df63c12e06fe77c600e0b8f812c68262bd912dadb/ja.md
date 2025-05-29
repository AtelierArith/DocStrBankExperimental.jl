```
collatz_upper_bound_L2_opnorm(A::BallMatrix; iterates=10)
```

行列 `A` の ℓ² ノルムに対する厳密な上限を Collatz 定理を用いて与えます。

ここではペロン理論を使用します：もし二つの行列に対して `B` が正で `|A| < B` であれば、ウィーラントの定理により ρ(A) <= ρ(B) が成り立ちます。[ウィーラントの定理](https://mathworld.wolfram.com/WielandtsTheorem.html)

キーワード引数 `iterates` は、Collatz の推定を使用する前に、1 のベクトルを何回繰り返すかを設定するために使用されます。
