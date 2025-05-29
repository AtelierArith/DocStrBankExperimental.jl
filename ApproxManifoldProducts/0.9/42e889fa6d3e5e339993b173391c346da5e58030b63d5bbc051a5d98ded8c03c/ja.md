```julia
manifoldProduct(ff; ...)
manifoldProduct(
    ff,
    mani;
    makeCopy,
    Niter,
    ndims,
    N,
    u0,
    oldPoints,
    addEntropy,
    recordLabels,
    selectedLabels,
    _randU,
    _randN,
    logger,
    bws
)

```

マンフォールド上の関数の積を点ごとに近似するために KernelDensityEstimate を使用します。

注意:

  * 常に完全な信念を渡してください。部分的なものを使用する場合は、例えば `partialDimsWorkaround=[1;3;6]` を使用します。
  * 異なる部分を一緒に掛け合わせることもできます。

## 例

```julia
# セットアップ
M = TranslationGroup(3)
N = 75
p = manikde!(M, [randn(3) for _ in 1:N])
q = manikde!(M, [randn(3) .+ 1 for _ in 1:N])

# ハイブリッドマンフォールド密度間の積を近似する
pq = manifoldProduct([p;q])

# 直接のヒストグラムプロット
using Gadfly
plot( x=getPoints(pq)[1,:], y=getPoints(pq)[2,:], Geom.histogram2d )

# TODO, 便利なプロット (進行中...)
```
