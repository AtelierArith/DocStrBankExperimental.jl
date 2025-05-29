```
ConfidenceBands(DM::DataModel, sol::AbstractODESolution, Xdomain::HyperCube; N::Int=300, plot::Bool=isloaded(:Plots)) -> Matrix
```

与えられた信頼区間 `sol` に対して、モデル予測の周りの点ごとの信頼帯は、信頼領域の境界でモデルを評価することによって `Xdomain` の x 値に対して計算されます。
