```julia
build(c::Connection, dir::Directory{<:Any}) -> ::Component{:div}
```

`Olive.Directory`のための`build`関数。この関数は新しいディレクトリタイプを作成するために拡張することができます。`import` `Olive.build`を使用して、新しい`build(c::Connection, dir::Directory{:custom})`バインディングを作成してください。
