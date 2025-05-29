```
MicrobiomeSample(name::String, metadata::Dictionary{Symbol, T}) <: AbstractSample
MicrobiomeSample(name::String; kwargs...)
MicrobiomeSample(name::String)
```

Microbiome sample type that includes a name and a [`Dictionary`](https://github.com/andyferris/Dictionaries.jl) of arbitrary metadata using `Symbol`s (other than `:name` or `:metadata`) as keys.

Metadata can be accessed using `getproperty` or `getindex` on the sample itself.

Samples can be instantiated with only a name, leaving the `metadata` `Dictionary` blank

Adding or changing metadata follows [the same rules](https://github.com/andyferris/Dictionaries.jl#accessing-dictionaries) as for the normal `Dictionary`.
