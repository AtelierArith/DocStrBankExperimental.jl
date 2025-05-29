```julia
load_inference(
    path::AbstractString;
    execution_provider,
    envname,
    logging_level,
    provider_options
) -> ONNXRunTime.InferenceSession

```

Load an ONNX file at `path` into an inference session.

*Keyword arguments:*

  * `execution_provider`: Either `:cpu` or `:cuda`. The latter requires a CUDA capable GPU and the `CUDA` and `cuDNN` packages must first be imported.
  * `envname`: Name used for logging purposes.
  * `logging_level`: Level of diagnostic output. Options are `:verbose`, `:info`, `:warning` (default), `:error`, and `:fatal`.
  * `provider_options`: Named tuple with options passed to the execution provider.

Note: Due to limitations of the C API `CreateEnv` function, `envname` and `logging_level` can only be set once per process. Attempts to change these are ignored.
