```
DistanceMatrixWithinStep(DM::AbstractDataModel, R::MultistartResults, Ind::Int; logarithmic::Bool=true, plot::Bool=isloaded(:Plots), kwargs...)
```

ステップ `Ind` における最適解間の相互距離の行列を返します。これは、ステップの最初のエントリに対するフィッシャー計量に関するものです。
