```
choimatrix(circuit::Vector{<:Any}; kwargs...) =
choimatrix(sites::Vector{<:Index}, circuit::Vector{<:Any}; kwargs...)
choimatrix(sites::Vector{<:Index}, circuit_tensors::Vector{<:ITensor};
           full_representation = false,kwargs...)
```

Compute the Choi matrix for a noisy channel

$$
\Lambda = (1+\mathcal{E})|\Phi\rangle\langle\Phi|^{\otimes n}
$$

If `full_representation = true`, the contraction is performed without approximation, leading to an output object whose size scales exponentiall with $n$
