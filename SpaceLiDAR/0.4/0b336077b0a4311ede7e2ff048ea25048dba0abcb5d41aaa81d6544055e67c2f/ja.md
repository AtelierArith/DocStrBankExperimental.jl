```
download!(granules::Vector{<:Granule}, folder=".")
```

[`download!`](@ref)と同様ですが、`granules`のベクター用です。aria2c（並列）を使用します。
