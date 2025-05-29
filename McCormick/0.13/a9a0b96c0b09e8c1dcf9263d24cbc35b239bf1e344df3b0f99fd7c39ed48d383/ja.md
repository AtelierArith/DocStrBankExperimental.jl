```julia
intersect(
    x::McCormick.MC{N, T<:Union{McCormick.MV, McCormick.NS}},
    y::McCormick.MC{N, T<:Union{McCormick.MV, McCormick.NS}}
) -> McCormick.MC{N, T} where {N, T<:Union{McCormick.MV, McCormick.NS}}

```

2つのMcCormickオブジェクトを交差させるには、`cv = max(cv1, cv2)`および`cc = min(cc1, cc2)`を適切なサブグラディエントで計算します。区間は通常の方法で交差します。通常の逆伝播スキームでは、丸め誤差により`cv > cc`になる可能性があることに注意してください。これは以下の方法で対処されます：

  * `cv - cc < MC_INTERSECT_TOL`かつ`diam(x.Intv ∩ y.Intv) > 3*MC_INTERSECT_TOL`の場合、

その場合、`cv = max(cv - MC_INTERSECT_TOL, Intv.lo)`および`cc = min(cc - MC_INTERSECT_TOL, Intv.hi)`とします。`cv == Intv.lo`または`cc == Intv.hi`の場合、サブグラディエントはゼロに設定されます。

  * `cv - cc < MC_INTERSECT_TOL`かつ`diam(x.Intv ∩ y.Intv) < 3*MC_INTERSECT_TOL`かつ

`MC_INTERSECT_NOOP_FALLBACK == true`の場合は、`x`を返します。

  * それ以外の場合は、`MC{N,T}(NaN, NaN, x.Intv ∩ y.Intv, ...)`を返します。
