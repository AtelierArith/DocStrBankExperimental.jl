```julia
stochastic_integral_transform(
    sys::ModelingToolkit.SDESystem,
    correction_factor
) -> ModelingToolkit.SDESystem

```

Choose correction_factor=-1//2 (1//2) to convert Ito -> Stratonovich (Stratonovich->Ito).
