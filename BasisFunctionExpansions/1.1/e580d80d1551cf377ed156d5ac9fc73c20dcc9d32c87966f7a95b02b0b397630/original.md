```
predict(model::LPVSS, x::AbstractMatrix, u, v=[x u])
```

If no `v` provided, return a prediction of the output `x'` given the state `x` and input `u` This function is called when a `model::LPVSS` object is called like `model(x,u)`

Provided `v`, return a prediction of the output `x'` given the state `x`, input `u` and scheduling parameter `v`
