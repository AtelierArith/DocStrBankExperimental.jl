```
layer(fs::Vector{T}, lower::Number, upper::Number,
      elements::ElementOrFunction...) where T <: Base.Callable -> [Layers]
```

Create a layer from a list of functions or expressions in `fs`.
