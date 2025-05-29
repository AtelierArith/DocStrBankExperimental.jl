```
channelview(A)
```

returns a view of `A`, splitting out (if necessary) the color channels of `A` into a new first dimension.

Of relevance for types like RGB and BGR, the channels of the returned array will be in constructor-argument order, not memory order (see `reinterpretc` if you want to use memory order).

# Example

```julia
img = rand(RGB{N0f8}, 10, 10)
A = channelview(img)   # a 3×10×10 array
```

See also: [`colorview`](@ref)
