```julia
struct GenericProjection{SRC<:DistributedFactorGraphs.InferenceVariable, TRG<:DistributedFactorGraphs.InferenceVariable, C, D} <: DistributedFactorGraphs.AbstractManifoldMinimize
```

一般的な射影、例えばカメラによるスパース特徴の観測:

```julia
camcal = CameraModels.PinholeCamera(480,640,410,410,241,319) # 簡単なモデルの例
sigma = [10 0; 0 10.0]
meas = (pixel_row,pixel_col)
gp = GenericProjection{
  Pose3,
  Point3
} = (
  MvNormal(
    meas,
    sigma
  ),
  camcal
)
```
