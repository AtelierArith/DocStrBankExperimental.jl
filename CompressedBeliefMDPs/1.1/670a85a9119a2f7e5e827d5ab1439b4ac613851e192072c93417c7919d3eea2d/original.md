```
make_numerical(B, pomdp)
```

Helper function that converts a set of beliefs `B` into a numerical matrix representation suitable for processing by numerical algorithms/compressors.

# Arguments

  * `B::Vector{<:Any}`: A vector of beliefs.
  * `pomdp::POMDP`: The POMDP model associated with the beliefs.

# Returns

  * `Matrix{Float64}`: A matrix where each row corresponds to a numerical representation of a belief in `B`.

# Example Usage

```julia
B = [belief1, belief2, belief3]
B_numerical = make_numerical(B, pomdp)
```
