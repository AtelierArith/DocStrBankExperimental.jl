```
uuid4([rng::AbstractRNG]) -> UUID
```

Generates a version 4 (random or pseudo-random) universally unique identifier (UUID), as specified by RFC 4122.

The default rng used by `uuid4` is not `GLOBAL_RNG` and every invocation of `uuid4()` without an argument should be expected to return a unique identifier. Importantly, the outputs of `uuid4` do not repeat even when `Random.seed!(seed)` is called. Currently (as of Julia 1.6), `uuid4` uses `Random.RandomDevice` as the default rng. However, this is an implementation detail that may change in the future.

!!! compat "Julia 1.6"
    The output of `uuid4` does not depend on `GLOBAL_RNG` as of Julia 1.6.


# Examples

```jldoctest
julia> rng = MersenneTwister(1234);

julia> uuid4(rng)
UUID("7a052949-c101-4ca3-9a7e-43a2532b2fa8")
```
