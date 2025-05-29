```
besselhx(nu, [k=1,] z)
```

スケーリングされたハンケル関数 $\exp(∓iz) H_ν^{(k)}(z)$ を計算します。ここで、$k$ は 1 または 2 であり、$H_ν^{(k)}(z)$ は `besselh(nu, k, z)` であり、$∓$ は $k=1$ の場合は $-$、$k=2$ の場合は $+$ です。 `k` は省略された場合、デフォルトで 1 になります。

この関数の理由は、$H_ν^{(k)}(z)$ が大きな $|z|$ に対して $\exp(∓iz)/\sqrt{z}$ に漸近的に比例するためであり、したがって `z` に大きな虚部があるときに [`besselh`](@ref) 関数はオーバーフローまたはアンダーフローの影響を受けやすいです。 `besselhx` 関数はこの指数関数的な因子を（解析的に）キャンセルするため、これらの問題を回避します。

外部リンク: [DLMF 10.2](https://dlmf.nist.gov/10.2), [Wikipedia](https://en.wikipedia.org/wiki/Bessel_function#Hankel_functions:_H(1)%CE%B1,_H(2)%CE%B1)

関連項目: [`besselh`](@ref)
