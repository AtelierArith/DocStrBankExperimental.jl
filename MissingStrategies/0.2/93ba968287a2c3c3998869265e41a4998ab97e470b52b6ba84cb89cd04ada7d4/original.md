Trait which contains all types with `Missing` in its element type (`eltype`),  excluding `Any`.

This allows dispatching on any Collection (Iterator, Vector, Tuple) that may contain missing elements.

See example of [`@handlemissings_stub`](@ref) for an application.
