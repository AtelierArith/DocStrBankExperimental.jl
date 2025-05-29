```julia
intersect(
    x::McCormick.MC{N, McCormick.Diff},
    y::McCormick.MC{N, McCormick.Diff}
) -> McCormick.MC{N, McCormick.Diff} where N

```

二つの `MC{N, Diff}` を微分可能性を保持する方法で交差させます。区間は通常の方法で交差します。典型的な逆伝播スキームでは、丸め誤差により `cv > cc` になる可能性があることに注意してください。これは以下の方法で対処されます：

  * もし `cv - cc < MC_INTERSECT_TOL` かつ `diam(x.Intv ∩ y.Intv) > 3*MC_INTERSECT_TOL` の場合、

その時 `cv = max(cv - MC_INTERSECT_TOL, Intv.lo)` かつ `cc = min(cc - MC_INTERSECT_TOL, Intv.hi)` とします。もし `cv == Intv.lo` または `cc == Intv.hi` の場合、サブ勾配はゼロに設定されます。

  * もし `cv - cc < MC_INTERSECT_TOL` かつ `diam(x.Intv ∩ y.Intv) < 3*MC_INTERSECT_TOL` かつ

`MC_INTERSECT_NOOP_FALLBACK == true` の場合は `x` を返します。

  * それ以外の場合は `MC{N,T}(NaN, NaN, x.Intv ∩ y.Intv, ...)` を返します。
