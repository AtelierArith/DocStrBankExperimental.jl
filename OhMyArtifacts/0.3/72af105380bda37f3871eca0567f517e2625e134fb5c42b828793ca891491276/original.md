```
download_my_artifact!([downloadf::Function = Downloads.download], url, name::AbstractString, artifacts_toml::String;
                     force_bind::Bool = false, bind_metadata = nothing, downloadf_kwarg...)
```

Convenient function that do download-create-bind together and return the content hash.  Download function `downloadf` should take two position arguments  (i.e. `downloadf(url, dest; downloadf_kwarg...)`). if `force_bind` is `true`,  it will overwrite the pre-existant binding.

See also: [create*my*artifact](@ref), [bind*my*artifact!](@ref)
