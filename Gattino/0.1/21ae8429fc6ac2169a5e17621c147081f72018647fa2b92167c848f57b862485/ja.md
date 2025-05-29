```julia
context(f::Function, width::Int64 = 500, height::Int64 = 720, margin::Pair{Int64, Int64} = 0 => 0) -> ::Context
```

この `context` のディスパッチは、2D `Context` を作成するために使用されます。マージンは `Pair{Int64, Int64}` として提供され、これがそれぞれ左と上のマージンです。

```example
con = context(500, 500) do con::Context
    text!(con, 250, 250, "hello world!")
end
```

`group` と `group!` の組み合わせを使用することで、指定されたスケーリングでレイヤーを構築できます。例えば、以下の `Context` は、この 500x500 フレームの左から 250px の位置から形状を描き始め、全高を消費します。適切なスケーリングのために、幅を 250 少なくしました。これにより、`Context` 内に 250px オフセットされ、幅 250px のスケーリングされたウィンドウが作成されますが、私たちのウィンドウは全くオフセットされておらず、幅 500px です。

```example
con = context(500, 500) do con::Context
    Gattino.text!(con, 250, 250, "hello world!")
    group(con, 250, 500, 250 => 0) do pointarea
        Gattino.points!(pointarea, [1, 2, 8, 4, 3, 4], 1, 2, 6, 7, 4, 5)
    end
end
```
