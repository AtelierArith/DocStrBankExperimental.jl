```julia
stochastic_integral_transform(
    sys::ModelingToolkit.SDESystem,
    correction_factor
) -> ModelingToolkit.SDESystem

```

correction_factor=-1//2 (1//2) を選択して Ito -> Stratonovich (Stratonovich->Ito) に変換します。
