```
position(sys::AbstractSystem, i)
```

Return the position of the ith particle if `i` is an `Integer`, a vector of  positions if `i` is a vector of integers, or a vector of all positions if  `i == :`.

The return type should be a vector of vectors each containing `D` elements that  are `<:Unitful.Length`.
