```
low_leveling(op, marker, mask; [dims])
low_leveling(op, marker, mask, se)
```

A function g is an lower leveling of a function f if and only if  for any couple of neighbouring pixels (p, q) g(p)>g(q)->g(p)>=f This algorithm modify marker to become a high_leveling of ref

The `dims` keyword is used to specify the dimension to process by constructing the box shape structuring element [`strel_box(marker; dims)`](@ref strel_box). For generic structuring element, the half-size is expected to be either `0` or `1` along each dimension.

# See also

[`high_leveling`](@ref),[`leveling`](@ref),  [`underbuild`](@ref),[`overbuild`](@ref)

# References

  * [1] 'From connected operators to levelings' [Meyer,1998] In ISMM '98: Proceedings of the fourth international symposium on Mathematical morphology and its applications to image and signal processingJune 1998 Pages 191–198
  * [2] 'Mathematical Morphology: From Theory to Applications' chap6 [Serra et al.] https://doi.org/10.1002/9781118600788.ch8
