```
tile(domain::CartesianIndices{N}, fraction::NTuple{N,Int}; cell_based=true) where {N}
```

`domain`を`fraction`で分割して小さなチャンクにします。これはCartesianIndexをサブドメインに分割するために設計されています。
