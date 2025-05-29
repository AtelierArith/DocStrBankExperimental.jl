Lobatto IIIF tableau with s stages

```julia
TableauLobattoIIIF(::Type{T}, s)
TableauLobattoIIIF(s) = TableauLobattoIIIF(Float64, s)
```

The constructor takes the number of stages `s` and optionally the element type `T` of the tableau.

References:

```
Wang Fangzong and Liao Xiaobing.
A Class of Lobatto Methods of Order 2s.
Journal of Applied Mathematics, Volume 46, Pages 6-10, 2016.
```
