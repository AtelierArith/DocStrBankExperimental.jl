```
function randomize!(
    instance::UnitCommitmentInstance;
    method = UnitCommitment.XavQiuAhm2021.Randomization();
    rng = MersenneTwister(),
)::Nothing
```

提供されたランダム化メソッドに従ってインスタンスのパラメータをランダム化します。

# 例

```julia
instance = UnitCommitment.read_benchmark("matpower/case118/2017-02-01")
UnitCommitment.randomize!(instance)
model = UnitCommitment.build_model(; instance)
```
