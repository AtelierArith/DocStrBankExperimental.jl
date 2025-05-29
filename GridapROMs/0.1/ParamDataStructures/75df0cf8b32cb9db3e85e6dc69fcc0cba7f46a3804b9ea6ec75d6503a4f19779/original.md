```
struct ParamSpace{P<:AbstractVector{<:AbstractVector},S<:SamplingStyle} <: AbstractSet{Realization}
  param_domain::P
  sampling_style::S
end
```

Fields:

  * `param_domain`: domain of definition of the parameters
  * `sampling_style`: distribution on `param_domain` according to which we can sample the parameters (by default it is set to `HaltonSampling`)
