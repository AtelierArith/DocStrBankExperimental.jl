Requires `import DataFrame`

```
detail(unk::MultiZAF, std::MultiZAF, θunk::AbstractFloat, θstd::AbstractFloat)::DataFrame

detail(mzs::AbstractArray{Tuple{MultiZAF,MultiZAF}}, θunk::AbstractFloat, θstd::AbstractFloat)
```

Tabulate each term in the `MultiZAF` matrix correction in a `DataFrame`.
