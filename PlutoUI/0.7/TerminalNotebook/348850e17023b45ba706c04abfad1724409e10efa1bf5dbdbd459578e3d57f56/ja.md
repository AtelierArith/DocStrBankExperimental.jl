```
with_terminal(f::Function; color::Bool=true, show_value::Bool=true)
```

関数を実行し、すべてのメッセージを `stdout` にキャプチャします。結果は、キャプチャされたテキストを表示する小さなターミナルになります。

これにより、`println`、`dump`、`Pkg.status` などからのメッセージを見ることができます。

例:

```julia
with_terminal() do
    x=1+1
    println(x)
    @warn "Oopsie!"
end 
```

```julia
with_terminal(show_value=false) do
    @time x=sum(1:100000)
end 
```

```julia
with_terminal(dump, [1,2,[3,4]])
```

詳細は [PlutoUI.Dump](@ref) を参照してください。
