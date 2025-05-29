```
tophatfilter(spec::Spectrum, filt::TopHatFilter{T}, scale::T = one(T))::FilteredUnknown where { T <: AbstractFloat }
```

未知のスペクトルをフィルタリングするためのものです。デフォルトは加重フィッティングモデルです。
