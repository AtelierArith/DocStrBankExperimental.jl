```
logspace(start::T, stop::T, N::Int)  where {T<:Number}
```

Generate logarithmic space.

Generate a logarithmic sequence of `N` numbers between  `start` and `stop` (i. e. sequence  of number with uniform intervals inbetween in the log space).

# Example

```
julia> logspace(2.0, 3.0, 5)                                                             
5-element Array{Float64,1}:                                                              
  100.0
  177.82794100389228   
  316.2277660168379      
  562.341325190349  
 1000.0    
```
