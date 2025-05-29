```julia
struct Canvas
    defs::Vector{Tuple{Int, Int}}
    code::Vector{Any}
    codelocs::Vector{Int32}
end
Canvas() = Canvas(Tuple{Int, Int}[], [], Int32[])
```

`Core` コードノードのための `Vector` のような抽象。

考慮すべきプロパティ：

1. どこにでも挿入するのは遅い。
2. 始めにプッシュするのは遅い。
3. 終わりにプッシュするのは速い。
4. 削除は速い。
5. 要素へのアクセスは速い。
6. 要素の設定は速い。

したがって、`Canvas` インスタンスを段階的に構築する場合、すべてが速くなるはずです。
