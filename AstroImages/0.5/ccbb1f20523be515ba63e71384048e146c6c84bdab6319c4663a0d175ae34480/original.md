Allows accessing and setting HISTORY header entries

```julia
img = AstroImage(randn(10,10))
push!(img, History, "2023-04-19: Added history entry.")
img[History] # ["2023-04-19: Added history entry."]
```
