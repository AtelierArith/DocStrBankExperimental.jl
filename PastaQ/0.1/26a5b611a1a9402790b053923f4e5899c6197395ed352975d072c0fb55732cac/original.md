```
tomography(data::Matrix{Pair{String, Int}}, sites::Vector{<:Index};
           method::String = "linear_inversion",
           fillzeros::Bool = true,
           trρ::Number = 1.0,
           max_iters::Int = 10000,
           kwargs...)

tomography(data::Matrix{Pair{String,Pair{String, Int}}}, sites::Vector{<:Index};
           method::String="linear_inversion", kwargs...)
```

Run full quantum tomography for a set of input measurement data `data`. If the input data consists of a list of `Pair{String, Int}`, it is interpreted as quantum state tomography. Each data point is a single measurement outcome, e.g. `"X" => 1` to refer to a measurement in the `X` basis with binary outcome `1`. If instead the input data is a collection of `Pair{String,Pair{String, Int}}`, it is interpreted as quantum process tomography, with each data-point corresponding to having input a given state to the channel, followed by a measurement in a basis, e.g.  `"X+" => ("Z" => 0)` referring to an input $|+\rangle$ state, followed by a measurement in the `Z` basis with outcome `0`.

There are three methods to perform tomography (we show state tomography here as an example):

1. `method = "linear_inversion"` (or `"LI"`): optimize a variational density matrix $\rho$ (or Choi matrix)1

2. `method = "least_squares"` (or `"LS"`):
3. `method = "maximum_likelihood"` (or `"ML"`):
