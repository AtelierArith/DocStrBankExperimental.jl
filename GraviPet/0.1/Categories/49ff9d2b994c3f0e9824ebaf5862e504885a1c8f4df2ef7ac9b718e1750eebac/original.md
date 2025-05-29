```
project(dst::T, src::Category)::T where {T<:Category}
```

Project the function `src` onto the representation given by `dst`. This can be used e.g. to sample Julia functions on a given grid, or to resample functiont on a different grid. `dst` can be a skeleton representation.
