2次の強安定保存法の2段階のタブローとCFL ≤ 1

```julia
TableauSSPRK2(::Type{T}=Float64) where {T}
```

コンストラクタは1つのオプション引数を取ります。それはタブローの要素型です。

これは[`TableauHeun2`](@ref)と同じタブローです。

参考文献:

```
Chi-Wang Shu, Stanley Osher.
Efficient implementation of essentially non-oscillatory shock-capturing schemes.
Journal of Computational Physics, Volume 77, Issue 2, Pages 439-471, 1988.
doi: 10.1016/0021-9991(88)90177-5.
Equation (2.16)
```
