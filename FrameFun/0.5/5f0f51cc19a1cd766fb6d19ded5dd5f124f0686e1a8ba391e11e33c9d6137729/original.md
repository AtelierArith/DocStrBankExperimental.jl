```
approximationproblem(args...)
```

# examples

## Create an approximationproblem from a dictionary

```jldocs
julia> approximationproblem(Fourier(10))
```

## Create an approximationproblem from a dictionary and a domain (extensionframe)

```jldocs
julia> approximationproblem(Fourier(10),0.0..0.5)
```

## Create an approximationproblem from a platform

```jldocs
julia> approximationproblem(FourierPlatform())
```

## Create an approximationproblem from a platform and a platform parameter

```jldocs
julia> approximationproblem(FourierPlatform(), 10)
```
