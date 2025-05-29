```
Annotation
```

# Constructors

```julia
Annotation(;angle, content, point_at)
```

# Keyword arguments

  * `angle::Real` is the angle of the pointer of the annotation.
  * `content::String` is the textual content of the annotation.
  * `point_at::Tuple{Real, Real}` specifies the location in the axis frame that the annotation should point at. A typical one would be `(1, 0)`, which means that the annotation points at the south-east corner of the axis frame.
