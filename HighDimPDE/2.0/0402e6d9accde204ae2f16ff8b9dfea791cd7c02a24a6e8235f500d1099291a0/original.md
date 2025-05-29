```julia
solve(
    prob::Union{HighDimPDE.PIDEProblem, HighDimPDE.ParabolicPDEProblem},
    alg::HighDimPDE.DeepSplitting,
    dt;
    batch_size,
    abstol,
    verbose,
    maxiters,
    use_cuda,
    cuda_device,
    verbose_rate
) -> HighDimPDE.PIDESolution{_A, _B, _C, Vector{T}, Vector{Any}, Nothing} where {_A, _B, _C, T}

```

Returns a `PIDESolution` object.

# Arguments

  * `maxiters`: number of iterations per time step. Can be a tuple, where `maxiters[1]` is used for the training of the neural network used in the first time step (which can be long) and `maxiters[2]` is used for the rest of the time steps.
  * `batch_size` : the batch size.
  * `abstol` : threshold for the objective function under which the training is stopped.
  * `verbose` : print training information.
  * `verbose_rate` : rate for printing training information (every `verbose_rate` iterations).
  * `use_cuda` : set to `true` to use CUDA.
  * `cuda_device` : integer, to set the CUDA device used in the training, if `use_cuda == true`.
