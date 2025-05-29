```
(o::InferenceSession)(inputs [,output_names])
```

Run an [`InferenceSession`](@ref) on a collection of inputs. Here `inputs` can either be a `NamedTuple` or an `AbstractDict`. Optionally `output_names` can be passed. In this case only the outputs whose names are contained in `output_names` are computed.
