```julia
continuation(
    prob,
    x0,
    par0,
    x1,
    p1,
    alg,
    lens,
    contParams;
    bothside,
    kwargs...
)

```

[Internal] この関数は直接呼び出すことを意図していません。

この関数は、最初の2つの点が渡される場合の[`continuation`](@ref)のアナログです（単一の点の代わりに）。したがって、`x0`は分岐上の最初の点（擬似弧長`s=0`）で、パラメータ`par0`を持ち、`x1`はパラメータ`set(par0, lens, p1)`を持つ2番目の点です。
