```julia
savename(
    prefix,
    params;
    digits,
    suffix,
    ignored_fields
) -> Union{Base.AnnotatedString{String}, String}

```

Generate file name from a set of parameters.

This is a replacement for the DrWatson function that has better handling of rounding and trailing zeros.
