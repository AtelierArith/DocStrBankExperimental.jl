```
AbstractFFTIndex{D}
```

Supertype for array indices that correspond to the frequency bins constructed by performing a Fourier transform of an array. This includes `FFTIndex{D}` and `NormalizedFFTIndex{D}`.

# Usage

`AbstractFFTIndex{D}` serves as an index for any object indexable by `CartesianIndex{D}`. Although there is no direct method of converting an `AbstractFFTIndex{D}` to a `CartesianIndex{D}`, as that requires information about the array being indexed, instances of this type can be used as an

Indexing an array with an `AbstractFFTIndex{D}` is guaranteed to be an inbounds access.

# Interface

For types `T<:AbstractFFTIndex{D}`:

  * The length of an `AbstractFFTIndex{D}` is always `D`.
  * The type constructors should accept a `Tuple{Vararg{Integer}}`. You will likely want to define

constructors that infer type parameters from the input. This will automatically define `T(x::Vararg{Integer,D})`.

  * `Tuple(::T)` should be defined, returning the index as a `NTuple{D,Int}`.
  * `convert(::Type{<:FFTIndex}, ::T)` should be defined. This is to allow for types that encode

information about normalization factors to be converted to an `FFTIndex` used by generic indexing methods. This will also automatically define `(::Type{<:FFTIndex})(::T)`.

Like `CartesianIndex{D}` in Julia 1.10 and up, `AbstractFFTIndex{D}` is a scalar type. To iterate through its components, convert it to a `Tuple` with the `Tuple` constructor.
