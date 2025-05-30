```
SlopeChangeConfig <: ChangesConfig
SlopeChangeConfig(; indicator = nothing, kw...)
```

[`estimate_changes`](@ref)に与えることができる設定です。これは、時系列に対して2つの接続された線形セグメントをフィッティングすることによって傾きの変化を推定し、結果（すなわち、2つの線形フィット）を[`SlopeChangeResults`](@ref)として返します。

現在、`SlopeChangeConfig`の結果の有意性は[`SlopeChangeSignificance`](@ref)を使用してのみ確認できます。

## キーワード引数

  * `indicator = nothing`: 関数 f(x) -> Real。傾きのフィッティングは、[`SlidingWindowConfig`](@ref)と同様に、スライディングウィンドウを介して推定される時系列の指標に対して行われます。これが`nothing`の場合、傾きの変化は時系列に直接適用されます。
  * `width_ind, stride_ind, whichtime`: `indicator`が`nothing`でない場合、[`SlidingWindowConfig`](@ref)と全く同じです。
