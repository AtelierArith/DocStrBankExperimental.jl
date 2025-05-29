```julia
evaluateManifoldNaive1D!(ret, idx, pts, bw, x)
evaluateManifoldNaive1D!(ret, idx, pts, bw, x, loo)
evaluateManifoldNaive1D!(ret, idx, pts, bw, x, loo, diffop)

```

等しい重みのガウスカーネルを共通のバンド幅で単純にKDEを評価します。ただし、この関数は、マニフォールド上の評価を許可します。
