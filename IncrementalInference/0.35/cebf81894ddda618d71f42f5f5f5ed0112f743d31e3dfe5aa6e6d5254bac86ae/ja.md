```julia
initVariable!(
    variable::DistributedFactorGraphs.VariableCompute,
    ptsArr::ApproxManifoldProducts.ManifoldKernelDensity;
    ...
)
initVariable!(
    variable::DistributedFactorGraphs.VariableCompute,
    ptsArr::ApproxManifoldProducts.ManifoldKernelDensity,
    solveKey::Symbol;
    dontmargin,
    N
)

```

変数を一連のポイントを使用して手動で初期化するためのメソッド。

ノート

  * `addFactor!(fg, ...; graphinit=false)`で自動グラフ初期化を無効にする

      * 初期化されていない変数は、`solveTree!`によって自動的に初期化されます。

例:

```julia
# fgにいくつかの変数が追加されます
addVariable!(fg, :somepoint3, ContinuousEuclid{2})

# データは(row,col) == (次元, サンプル)として整理されます
pts = randn(2,100)
initVariable!(fg, :somepoint3, pts)

# マニフォールド管理は自動的に行われるべきです。
# Manifolds.jlとの統合のためのアップグレードが来る予定です。RoME #244を参照してください。

## 既存のファクターを使用してinitVariable!を行うことも可能です。例えば、
initVariable!(fg, :x3, [:x2x3f1])
```

DevNotes

  * TODO graphinitとtreeinitをより良く文書化する。
