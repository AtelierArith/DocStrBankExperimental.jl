```
signature(::Type{AbstractSignature}, object, timestamp, data) -> String
```

Compute a verifiable checksum for the given `object`, `timestamp`, and `data`.

Extended by packages that bring in the required cryptographic libraries. The extender of `signature` must define their own subtype of `AbstractSignature` to use in their method signature.

# Examples

```julia
struct MySignature <: AbstractSignature
    # ...
end

signature(::Type{MySignature}, object, timestamp, data) = # ...
```

Along with `signature` the extender must also extend `is_signed` and `verify` to work with their new type.
