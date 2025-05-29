# Function call

`usprint(u,U)`

# Description

Returns a string containing the number with six digits plus unit without space in between, such that the string output can be copied and pasted.

# Variables

`u` Variable to be processed

`U` Optional target unit; if not provided, the actual unit is used

# Examples

```julia julia> I1 = 1mA julia> usprint(I1) 1mA julia> usprint(I1, A) 0.001A
