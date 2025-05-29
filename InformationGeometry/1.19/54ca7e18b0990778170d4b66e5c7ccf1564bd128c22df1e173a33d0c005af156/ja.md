```
ApproxConfidenceBands(DM::AbstractDataModel, ParameterCube::HyperCube, Xdomain=XCube(DM); N::Int=300, plot::Bool=isloaded(:Plots))
```

`ParameterCube`の面の中心に関連する信頼帯を計算します。`ParameterCube`が特定の信頼領域を囲む場合、これは通常、この信頼レベルに関連する真の点ごとの信頼帯の大まかで非対称な過大評価をもたらします。
