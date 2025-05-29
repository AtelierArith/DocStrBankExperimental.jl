```julia
group(f::Function, c::AbstractContext, w::Int64 = c.dim[1],
    h::Int64 = c.dim[2], margin::Pair{Int64, Int64} = c.margin) -> ::Nothing
```

`c`、`Context`（または`Group`）上に*スケーリンググループ*を作成します。これはレイヤーを作成するのではなく、スケーリングウィンドウのみを作成します。これは同じ方法で`Group`を作成しますが、その子を`c`の子に描画します。レイヤーには`group!`を使用してください。

```example

```
