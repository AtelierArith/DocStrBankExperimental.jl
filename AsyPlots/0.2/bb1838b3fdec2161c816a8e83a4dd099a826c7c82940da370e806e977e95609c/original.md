```
Arrow(name::AbstractString,
      size::Real,
      position::Real)
```

Store instructions for drawing an arrow

`position` is an element of [0,1] which indicates how far along the path the arrow should be drawn

NoArrow() returns a no-arrow instruction, while Arrow3() gives an arrow suitable for 3D paths
