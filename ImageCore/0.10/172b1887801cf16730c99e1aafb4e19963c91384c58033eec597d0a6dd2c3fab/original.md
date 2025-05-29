```
colorview(C, A)
```

returns a view of the numeric array `A`, interpreting successive elements of `A` as if they were channels of Colorant `C`.

Of relevance for types like RGB and BGR, the elements of `A` are interpreted in constructor-argument order, not memory order (see `reinterpretc` if you want to use memory order).

# Example

```jl
A = rand(3, 10, 10)
img = colorview(RGB, A)
```

See also: [`channelview`](@ref)
