```
IncrementalTimeSeriesFit(DM::AbstractDataModel, initial::AbstractVector{<:Number}=MLE(DM); steps::Int=length(Data(DM))÷5, Method::Function=InformationGeometry.minimize, kwargs...) -> Vector
```

データモデルをインクリメンタルにフィットさせるために、時系列をチャンクに分割します。例えば、最初の四分の一のデータポイントのみをフィットさせ、その後半分、そしてその後と続けます。これにより、特に自己相関のある時系列データにおいて、ランダムなスタートポイントからはるかに良いフィッティング結果が得られることがあります。例えば、時系列データが振動する場合、最適化がしばしば局所最適解に陥り、モデルがデータを通してほぼ直線をフィットさせ、振動を正しく認識しないことがあります。
