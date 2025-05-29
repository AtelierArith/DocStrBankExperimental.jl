```
rv!(turtle, strength)
```

Rotates the turtle towards the Z axis. The angle of rotation is proportional to the cosine of the zenith angle of the turtle (i.e., angle between its head and the vertical axis) with the absolute value of `strength` being the proportion between the two. `strength` should vary between -1 and 1. If `strength` is negative, the turtle rotates downwards (i.e., towards negative values of Z axis), otherwise upwards.

## Examples

```jldoctest
julia> turtle = Turtle();

julia> ra!(turtle, 45.0);

julia> rv!(turtle, 0.5);
```
