```
ネットCDFファイルを開く、`nc_open`は`NCDataset`のエイリアスです
```

```julia
nc_open(
    f::Union{AbstractString, Vector{<:AbstractString}},
    args...;
    kwargs...
) -> Any

```

# 引数

  * `mode`:

      * "a": 追加
      * "c": 作成

# 例

```julia
nc_open(f, args; kwargs...)
```

[`packages/NetCDFTools/QX4TD/src/nc_info.jl:20`](file:///home/terasaki/.julia/packages/NetCDFTools/QX4TD/src/nc_info.jl)で定義されています。

@seealso [NCDatasets.NCDataset()]
