```
macro parameters(args...)
```

Create a `SimulationParameters` with the actual struct type being determined by the arguments passed to the macro.

# Examples

```julia
# Create a StructArray{T₁T₂} with T₁ and T₂ values
T₁, T₂ = rand(100), 0.1*rand(100)
parameters = @parameters T₁ T₂

# Create a StructArray{T₁T₂B₁} with T₁, T₂ and B₁ values
T₁, T₂, B₁ = rand(100), 0.1*rand(100), ones(100)
parameters = @parameters T₁ T₂ B₁

# Create a StructArray{T₁T₂B₀} with T₁, T₂ and B₀ values
# This time use the aliases that don't use unicode characters
T1, T2, B0 = rand(100), 0.1*rand(100), ones(100)
parameters = @parameters T1 T2 B0
```
