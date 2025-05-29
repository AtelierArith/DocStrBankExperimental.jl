```
two_ray_propagation( distance::Real, transmit_height::Real, receive_height::Real, frequency_hz::Real, Γ::Real )::Complex
```

Calculate the two-way two-ray propagation between two points above a flat plane. Returns the propagation factor F. The one-way power propagation factor is |F|².

# Arguments

  * `distance`       	The distance parallel to the plane earth.
  * `transmit_height`	The height of the transmitter above the plane earth.
  * `receive_height` 	The height of the receiver/target above the plane earth.
  * `Γ`             	The reflection coefficient of the medium of the plane earth.

## Examples

```jldoctest
julia> res = two_ray_propagation( 2e3, 10, 12, 20e9, -1 );

julia> round(res, digits=6)
1.999395 + 0.034791im
```

## References

  * Radar Systems Engineering Lecture 5 Propagation through the Atmosphere, IEEE New Hampshire Section IEEE AES Society, 2010
