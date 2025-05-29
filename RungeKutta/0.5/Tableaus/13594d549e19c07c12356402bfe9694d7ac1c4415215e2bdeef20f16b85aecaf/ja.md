3次の強安定保存法の表で、3つのステージとCFL ≤ 1

```julia
TableauSSPRK3(::Type{T}=Float64) where {T}
```

コンストラクタは1つのオプション引数を取ります。それは表の要素型です。

参考文献:

```
Chi-Wang Shu, Stanley Osher.
Efficient implementation of essentially non-oscillatory shock-capturing schemes.
Journal of Computational Physics, Volume 77, Issue 2, Pages 439-471, 1988.
doi: 10.1016/0021-9991(88)90177-5.
Equation (2.18)
```
