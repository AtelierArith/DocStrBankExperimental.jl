```
generate_support_values(domain::AbstractInfiniteDomain,
                        [method::Type{MyMethod} = MyMethod];
                        [num_supports::Int = DefaultNumSupports,
                        sig_digits::Int = DefaultSigDigits]
                        )::Tuple{Array{<:Real}, Symbol}
```

A multiple dispatch method for [`generate_supports`](@ref). This will return a tuple where the first element are the supports and the second is their label. This can be extended for user-defined infinite domains and/or generation methods. When defining a new domain type the default method dispatch should make `method` an optional argument (making it the default). Otherwise, other method dispatches for a given domain must ensure that `method` is positional argument without a default value (contrary to the definition above). Note that the  `method` must be a subtype of either [`PublicLabel`](@ref) or [`InternalLabel`](@ref).
