```
decode(decoder, code, syndrome::AbstractVector{Bool}; kwargs...) -> DecodeResult
```

Resolve a recovery operation for the given `code` and `syndrome`, or evaluate the success of decoding, as encapsulated in the decode result.

The syndrome has length equal to the number of code stabilizers, and element values of 0 or 1 (false or true) indicate whether the corresponding stabilizer does or does not commute with the error, respectively.

Keyword parameters `kwargs` may be provided by the client, e.g. [`App`](@ref App), with context values such as `error_model`, `error_probability` and `error`. Most implementations will ignore such parameters; however, if they are used, implementations should declare them explicitly and treat them as optional.

See also [`DecodeResult`](@ref).

!!! note "Abstract method"
    This method should be implemented for concrete subtypes or duck-typed implementations of [`Decoder`](@ref).

