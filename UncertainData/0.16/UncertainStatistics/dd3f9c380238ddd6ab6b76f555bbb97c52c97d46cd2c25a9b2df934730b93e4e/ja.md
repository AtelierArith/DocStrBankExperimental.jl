```
cov(d1::AbstractUncertainValueDataset, d2::AbstractUncertainValueDataset; kwargs...)
```

2つの不確実なデータセット `d1` と `d2` の間の共分散の単一推定値を取得します。これは、両方のデータセットを独立に再サンプリングすることによって行われます。つまり、まず `d1` の不確実な値を提供する分布に従って `d1` の実現を引きます。次に、`d2` の提供する分布に従って `d2` の実現を引きます。これら2つの引き出し/実現は、現在両方とも長さ `L = length(d1) = length(d2)` のベクトルです。最後に、これらの引き出しの間の共分散を計算します。これにより、`d1` と `d2` の間の共分散の単一推定値が得られます。
