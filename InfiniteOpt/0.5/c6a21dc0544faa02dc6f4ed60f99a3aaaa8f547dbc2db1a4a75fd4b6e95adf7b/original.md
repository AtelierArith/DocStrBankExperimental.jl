```
num_derivatives(model::InfiniteModel)::Int
```

Returns the number of derivatives that have been defined in `model`. Note that  nested derivatives will be counted in accordance with their components (e.g.,  $\frac{d^2 x(t)}{dt^2} =$\frac{d}{dt}\left(\frac{d x(t)}{dt} \right)``  will count as 2 derivatives.)

**Example**

```julia-repl
julia> num_derivatives(model)
12
```
