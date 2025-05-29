```
MatrixOrdering(matrix)
MatrixOrdering(Vector{Vector})
```

Matrix monomial ordering. 

## Example

```@example
using Groebner, AbstractAlgebra
R, (x, y, z, w) = QQ["x", "y", "z", "w"];

# the number of columns equal to the number of variables
ord = MatrixOrdering(
    [x,y,z,w],
    [
    1 0  0  2;
    0 0  1  2;
    0 1  1  1;
    ])
groebner([x*y + w, y*z - w], ordering=ord)
```
