```
IsStochasticInteger{T=Int}() <: StochasticStyle{T}
```

整数ウォーカーを用いたFCIQMCアルゴリズムは、[Booth *et al.* (2009)](https://doi.org/10.1063/1.3193710)に従っています。ベクトル行列積の間、各個別の対角線および生成ステップは、近くの整数値に確率的に丸められます。

[`StochasticStyle`](@ref)も参照してください。
