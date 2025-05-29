```julia
WrappedRNG{R, T1, T2} <: AbstractRNG{T2}
WrappedRNG(base_rng, T2)
WrappedRNG(R, T2, args...)
```

Wrap a RNG which originally provides output in T1 into a RNG that provides output in T2.

# Examples

```jldoctest
julia> r = Xorshifts.Xorshift128Star(123);

julia> RandomNumbers.output_type(r)
UInt64

julia> r1 = WrappedRNG(r, UInt32);

julia> RandomNumbers.output_type(r1)
UInt32

julia> r2 = WrappedRNG(Xorshifts.Xorshift128Star, UInt32, 123);

julia> RandomNumbers.output_type(r2)
UInt32

julia> @Test.test rand(r1, UInt32, 3) == rand(r2, UInt32, 3)
Test Passed
```
