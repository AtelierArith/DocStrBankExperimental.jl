```
correct_deprecated_properties!(orig_properties::T, new_properties::T, deprecated_properties::T)::Tuple{T,T} where T <: Dict{String,Any}
```

Helper function for correcting properties that have been deprecated in `orig_properties` into `new_properties`
