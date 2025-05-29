```
jldsave(filename; kwargs...)
jldsave(filename, compress; kwargs...)
jldsave(filename, compress, iotype; kwargs...)
```

`filename`にJLD2ファイルを作成し、キーワード引数として与えられた変数を保存します。

# 例

```julia
jldsave("example.jld2"; a=1, b=2, c)
```

は次のように等価です。

```julia
jldopen("example.jld2", "w") do f
    f["a"] = 1
    f["b"] = 2
    f["c"] = c
end
```

デフォルトの`MmapIO`の代わりに`IOStream`のioタイプを選択するには、`jldsave(fn, IOStream; kwargs...)`を使用します。
