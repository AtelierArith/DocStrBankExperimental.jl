```
rgbcolor(col::Any)
```

Return Colors.RGB object from string or symbol. 

```jldoctest
julia> rgbcolor(:red)
RGB{Float64}(1.0, 0.0, 0.0)

julia> rgbcolor("red")
RGB{Float64}(1.0, 0.0, 0.0)
```
