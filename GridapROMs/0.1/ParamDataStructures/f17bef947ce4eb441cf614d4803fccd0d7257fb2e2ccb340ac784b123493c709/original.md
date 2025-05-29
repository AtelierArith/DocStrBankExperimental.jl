```
struct TransientParamSpace{P<:ParamSpace,T} <: AbstractSet{TransientRealization}
  parametric_space::P
  temporal_domain::T
end
```

Fields:

  * `parametric_space`: underlying parameter space
  * `temporal_domain`: underlying temporal space

It represents, in essence, the set of tuples (p,t) in `parametric_space` × `temporal_domain`
