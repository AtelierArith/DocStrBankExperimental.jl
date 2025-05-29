```
connect(output_connector, ap_name::Symbol, input_connector; verbose = true)
connect(output_connector, ap::AnalysisPoint, input_connector; verbose = true)
```

Connect `output_connector` and `input_connector` with an [`AnalysisPoint`](@ref) inbetween. The incoming connection `output_connector` is expected to be an output connector (for example, `ModelingToolkitStandardLibrary.Blocks.RealOutput`), and vice versa.

*PLEASE NOTE*: The connection is assumed to be *causal*, meaning that

```julia
@named P = FirstOrder(k = 1, T = 1)
@named C = Gain(; k = -1)
connect(C.output, :plant_input, P.input)
```

is correct, whereas

```julia
connect(P.input, :plant_input, C.output)
```

typically is not (unless the model is an inverse model).

# Arguments

  * `output_connector`: An output connector
  * `input_connector`: An input connector
  * `ap`: An explicitly created [`AnalysisPoint`](@ref)
  * `ap_name`: If a name is given, an [`AnalysisPoint`](@ref) with the given name will be created automatically.

# Keyword arguments

  * `verbose`: Warn if an input is connected to an output (reverse causality). Silence this warning if you are analyzing an inverse model.
