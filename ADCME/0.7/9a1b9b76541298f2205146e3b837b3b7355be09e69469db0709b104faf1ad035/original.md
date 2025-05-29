```
ae_to_code(file::String, scope::String; activation::String = "tanh")
```

Return the code string from the feed-forward neural network data in `file`. Usually we can immediately evaluate  the code string into Julia session by 

```julia
eval(Meta.parse(s))
```

If `activation` is not specified, `tanh` is the default. 
