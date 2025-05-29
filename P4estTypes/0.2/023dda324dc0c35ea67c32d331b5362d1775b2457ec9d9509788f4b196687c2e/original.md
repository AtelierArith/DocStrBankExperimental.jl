```
function Connectivity{X}(vertices::AbstractVector, cells::AbstractVector) where {X}

Example:
'''julia
 julia> vertices = [
            (0.0, 0.0, 0.0),
            (0.0, 0.0, 1.0),
            (0.0, 1.0, 0.0),
            (0.0, 1.0, 1.0),
            (1.0, 0.0, 0.0),
            (1.0, 0.0, 1.0),
            (1.0, 1.0, 0.0),
            (1.0, 1.0, 1.0),
        ]
 julia> cells = [
            Int32.((1, 3, 2, 4)),
            Int32.((4, 3, 8, 7)),
            Int32.((7, 5, 8, 6)),
            Int32.((6, 2, 5, 1)),
            Int32.((1, 3, 5, 7)),
            Int32.((2, 4, 6, 8)),
        ]
 julia> conn = Connectivity{4}(vertices, cells)
'''
   6--------8    cell 1 connects vertices 1, 3, 2, 4
  /        /|    cell 2 connects vertices 4, 3, 8, 7
 /        / |    .
2--------4  |    .
|        |  |    .
|  5     |  7    cell 6 connects vertices 2, 4, 6, 8
|        | /
|        |/
1--------3
```
