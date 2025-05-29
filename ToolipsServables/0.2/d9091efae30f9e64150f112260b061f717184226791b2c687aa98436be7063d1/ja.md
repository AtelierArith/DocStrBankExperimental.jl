```julia
tmd(name::String, md::String = "", args::Pair{String, <:Any} ...; args ...) -> ::Component{:div}
```

生のマークダウン文字列から直接`Component`を作成します。`Component`の子は、提供されたマークダウンがHTMLにレンダリングされたものになります。

```example
mymd = "# hello\n **this** is markdown"

comp = tmd("mygreeting", mymd)
```
