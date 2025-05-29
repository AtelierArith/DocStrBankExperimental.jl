```
ngonside(centerpoint::Point, sidelength::Real, sides::Int=5, orientation=0;
        action=:none,
        vertices=false,
        reversepath=false)
ngonside(centerpoint::Point, sidelength::Real, sides::Int, orientation, action;
        vertices=false,
        reversepath=false)
```

Draw a regular polygon centered at `centerpoint` with `sides` sides of length `sidelength`.
