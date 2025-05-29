```
updateparam(P::Process, p::Integer, profile::Function)
updateparam(P, p, value::Union{Number, Tuple, Vector})
updateparam(P, p, profile, value)
```

Copy a [`Process`](@ref) with a new set of `:parameter_profiles` and `:parameter_profile_parameters`. `p` is an integer specifying which parameter to update, `profile` is the new profile, and `value` contains the new `:parameter_profile_parameters`.
