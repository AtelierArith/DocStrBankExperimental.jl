```
tophatfilter(spec::Spectrum, filt::TopHatFilter{T}, scale::T = one(T))::FilteredUnknown where { T <: AbstractFloat }
```

For filtering the unknown spectrum. Defaults to the weighted fitting model.
