```
get_var(
    filename       ::String,
    params         ::Dict{String,String},
    varnr          ::Integer,
    precision      ::DataType=Float32;
    slicex         ::AbstractVector{<:Integer}=Int[],
    slicey         ::AbstractVector{<:Integer}=Int[],
    slicez         ::AbstractVector{<:Integer}=Int[]
    )
```

`filename`から変数番号`varnr`を読み込みます。変数は主変数または補助変数のいずれかです。スナップショットのスライスはオプションです。デフォルトでは単精度スナップショットを想定しています。
