```
add_generative_supports(pref::IndependentParameterRef)::Nothing
```

Create generative supports for `pref` if needed in accordance with its  generative support info using [`make_generative_supports`](@ref) and add them to  `pref`. This is intended as an internal function, but can be useful user defined  optimizer model extensions that utlize our support system.
