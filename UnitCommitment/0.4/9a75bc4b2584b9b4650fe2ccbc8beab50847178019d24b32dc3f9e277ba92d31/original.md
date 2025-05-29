```
function randomize!(
    instance::UnitCommitmentInstance;
    method = UnitCommitment.XavQiuAhm2021.Randomization();
    rng = MersenneTwister(),
)::Nothing
```

Randomizes instance parameters according to the provided randomization method.

# Example

```julia
instance = UnitCommitment.read_benchmark("matpower/case118/2017-02-01")
UnitCommitment.randomize!(instance)
model = UnitCommitment.build_model(; instance)
```
