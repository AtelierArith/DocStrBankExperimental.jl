```
get_var(
    expname ::String,
    snap    ::Union{<:Integer, AbstractVector{<:Integer}},
    expdir  ::String,
    variable::String,
    args...
    ;
    kwargs...
)
```

Bifrost実験の実験ディレクトリ`expdir`と実験名`expname`を使用して、1つまたは複数のスナップショットから`variable`をロードします。
