```
read_gmt(fn)
```

GMTファイル（MSigDB遺伝子セット形式）を読み込みます。ここで、`fn`はファイルパスです。

# 例

```jldoctest
julia> res = read_gmt("h.all.v7.5.1.symbols.gmt")

julia> gn, gs = read_gmt("h.all.v7.5.1.symbols.gmt")

```
