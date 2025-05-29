```
retract(M::AbstractManifold, p, X, method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)))
retract!(M::AbstractManifold, q, p, X, method::AbstractRetractionMethod=default_retraction_method(M, typeof(p)))
```

点 `p` から方向 `X` へのスケール `t` を持つ [`exp`](@ref) 指数写像の近似版である再tractionを [`AbstractManifold`](@ref) `M` 上で計算します。これは `q` のインプレースで計算できます。

再traction $\operatorname{retr}_p: T_p\mathcal M → \mathcal M$ は、次の条件を満たす滑らかな写像です。

1. $$
    \operatorname{retr}_p(0) = p
    $$
2. $$
    D\operatorname{retr}_p(0): T_p\mathcal M → T_p\mathcal M
    $$

    は恒等写像です。

すなわち、$D\operatorname{retr}_p(0)[X]=X$ がすべての $X∈ T_p\mathcal M$ に対して成り立ちます。

ここで、$D\operatorname{retr}_p$ は再tractionの微分を示します。

再tractionは、すべての $X$ に対して曲線 $c(t) = R_p(tX)$ が $t=0$ でゼロ加速度を持つ場合、すなわち $c''(0) = 0$ であるとき、二次のものと呼ばれます。

再tractionメソッドは最後の引数で指定でき、デフォルトは [`default_retraction_method`](@ref)`(M)` です。利用可能な再tractionの詳細については、各マニフォールドのドキュメントを参照してください。

局所的に、再tractionは可逆です。逆操作については [`inverse_retract`](@ref) を参照してください。
