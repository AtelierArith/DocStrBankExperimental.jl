```
box_approximation(R::Rectification{N}) where {N}
```

Overapproximate the rectification of a set by a tight hyperrectangle.

### Input

  * `R`– rectification of a set

### Output

A hyperrectangle.

### Algorithm

Box approximation and rectification distribute. We first check whether the wrapped set is empty. If so, we return the empty set. Otherwise, we compute the box approximation of the wrapped set, rectify the resulting box (which is simple), and finally convert the resulting set to a box.
