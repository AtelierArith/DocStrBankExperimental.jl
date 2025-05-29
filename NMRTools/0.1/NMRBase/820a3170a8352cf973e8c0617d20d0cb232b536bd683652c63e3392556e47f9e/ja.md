```
acqus(nmrdata)
acqus(nmrdata, key)
acqus(nmrdata, key, index)
```

Bruker acqusファイルからデータを返します。存在しない場合は`nothing`を返します。キーはシンボルまたは文字列として渡すことができます。キーが指定されていない場合、acqusファイル全体を表す辞書が返されます。

存在する場合、`vclist`や`vdlist`などの補助ファイルの内容にこの関数を使用してアクセスできます。

# 例

```julia-repl
julia> acqus(expt, :pulprog)
"zgesgp"
julia> acqus(expt, "TE")
276.9988
julia> acqus(expt, :p, 1)
9.2
julia> acqus(expt, "D", 1)
0.1
julia> acqus(expt, :vclist)
11-element Vector{Int64}:
[...]
```

詳細は[`metadata`](@ref)を参照してください。
