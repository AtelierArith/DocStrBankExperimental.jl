```
normalize(h::Histogram{T,N}, aux_weights::Array{T,N}...; mode::Symbol=:pdf) where {T,N}
```

Normalize the histogram `h` and rescales one or more auxiliary weight arrays at the same time (`aux_weights` may, e.g., contain estimated statistical uncertainties). The values of the auxiliary arrays are scaled by the same factor as the corresponding histogram weight values. Returns a tuple of the normalized histogram and scaled auxiliary weights.
