```
runtests(args::Vector{String})
```

ファイル `test/runtests.jl` を含め、`args` の正規表現に一致するテストセットを実行します（先頭に '-' または '¬' が付いている場合、その表現に一致するテストは除外されることを示します）。

# 例

```jldoctest
julia> runtests(["t/a/.*"])         # `t/a` の下のすべてのテストを実行

julia> runtests(["t/.*", "¬t/b/2"])  # `t` の下のすべてのテストを実行するが `t/b/2` は除外
```
