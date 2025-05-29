```
intersects(geometry₁, geometry₂)
```

Tells whether or not `geometry₁` and `geometry₂` intersect.

## References

  * Gilbert, E., Johnson, D., Keerthi, S. 1988. [A fast Procedure for Computing the Distance Between Complex Objects in Three-Dimensional Space](https://ieeexplore.ieee.org/document/2083)

### Notes

The fallback algorithm works with any geometry that has a well-defined [`supportfun`](@ref).
