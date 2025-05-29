```
active(win::Window)::Bool
active(connection)::Bool
```

指定された `Window`（または `Page`、`shell`、または他の内部コンポーネント）が現在「アクティブ」であるかどうかを示します。つまり、それはそのElectronコンポーネントへのオープン接続を持っています。

```julia-repl
julia> w = Window();

julia> active(w)
true

julia> close(w)

julia> active(w)
false
```
