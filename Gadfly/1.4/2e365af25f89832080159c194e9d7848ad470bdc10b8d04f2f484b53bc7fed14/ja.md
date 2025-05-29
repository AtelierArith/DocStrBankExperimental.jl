```
layer(fs::Vector{T}, lower::Number, upper::Number,
      elements::ElementOrFunction...) where T <: Base.Callable -> [Layers]
```

`fs`の関数または式のリストからレイヤーを作成します。
