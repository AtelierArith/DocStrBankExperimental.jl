```
spec(name::Symbol)::GroupSpec
```

Gets a group specification from a provided canonical `name` of the group specification which are hardcoded into the library. 

# Examples

```julia
# NIST elliptic curve P-192 specification:
p192_spec = spec(:P_192)
P192 = concretize_type(ECGroup, p192_spec)

# Modular prime group specification
modp_spec = spec(:RFC5114_2048_224)
MODP = concretize_type(PGroup, modp_spec)
```

See also `concretize_type`, `@ECGroup`, `@PGroup`
