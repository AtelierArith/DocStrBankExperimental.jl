```
cube_field_size(cube::String)
```

Determine the field sizes of a given cube label.

The function returns the dimension of the ambient space in the first output parameter `pointdim`, and the length of the individual coordinate fields in the second return variable `pointlen`.

# Example

```jldoctest
julia> cube_field_size("011654003020.0110")
(4, 3)
```
