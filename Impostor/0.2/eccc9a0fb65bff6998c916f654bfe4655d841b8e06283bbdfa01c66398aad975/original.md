```
is_locale_available(p::T, c::T, l::T) :: Bool where {T <: AbstractString}
```

Return whether the provided locale `l` is available for content `c` from provider `p`.

# Parameters

  * `p::AbstractString`: provider name
  * `c::AbstractString`: content name
  * `l::AbstractString`: locale name
