```julia
read_model_file(
    model_filepath::AbstractString;
    factor_eltype
) -> TensorInference.UAIModel

```

Parse the problem instance found in `model_filepath` defined in the UAI model format. If the provided file path is empty, return `nothing`.

The UAI file formats are defined in: https://uaicompetition.github.io/uci-2022/file-formats/
