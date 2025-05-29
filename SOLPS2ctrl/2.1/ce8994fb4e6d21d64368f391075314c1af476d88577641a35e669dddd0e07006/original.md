```
extrapolate_core(
    edge_rho::Vector{Float64},
    edge_quantity::Vector{Float64},
    rho_output::Vector{Float64},
)::Vector{Float64}
```

Function for assuming a core profile when given edge profile data.

Concept:

1. value and derivative should be continuous when joining real data
2. derivative at magnetic axis is known to be 0 when making profile vs. rho, by the definition of rho
3. derivative probably does something fancier between the pedestal and axis than just linear interpolation, so add an extra point in there
4. there's a joint between the steep pedestal and the shallow core that needs an extra knot to manage it properly
5. after making up a very simple gradient profile out of a few line segments, integrate it to get the profile of the quantity in question
