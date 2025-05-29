```
realization(p::ParamSpace;nparams=1,sampling=get_sampling_style(p),kwargs...) -> Realization
realization(p::TransientParamSpace;nparams=1,sampling=get_sampling_style(p),kwargs...) -> TransientRealization
```

Extraction of a set of `nparams` parameters from a given parametric space, by default according to the sampling strategy specified in `p`.
