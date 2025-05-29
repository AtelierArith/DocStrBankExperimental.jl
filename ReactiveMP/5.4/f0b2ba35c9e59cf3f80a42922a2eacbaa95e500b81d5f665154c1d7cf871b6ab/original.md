```
StandardBasisVector{T, len, ind}(scale::T)
```

`StandardBasisVector` creates a standard Cartesian basis vector of zeros of length `len` with a single element `scale` at index `ind`.

An example is the 3-dimensional standard basis vector for the first dimension

$$
e = \begin{bmatrix} 1 \\ 0 \\ 0 \end{bmatrix}
$$

Which can be constructed by calling `e = StandardBasisVector(3, 1, 1)`
