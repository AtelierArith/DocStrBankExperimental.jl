```
eigenbox(A[, method=Rohn()])
```

Returns an enclosure of all the eigenvalues of `A`. If `A` is symmetric, then the output is a real interval, otherwise it is a complex interval.

### Input

  * `A` – square interval matrix
  * `method` – method used to solve the symmetric interval eigenvalue problem (bounding   eigenvalues of general matrices is also reduced to the symmetric case).   Possible values are

    ```
    - `Rohn` -- (default) fast method to compute an enclosure of the eigenvalues of
          a symmetric interval matrix
    - `Hertz` -- finds the exact hull of the eigenvalues of a symmetric interval
          matrix, but has exponential complexity.
    ```

### Algorithm

The algorithms used by the function are described in [[HLA13]](@ref).

### Notes

The enclosure is not rigorous, meaning that the real eigenvalue problems solved internally utilize normal floating point computations.

### Examples

```jldoctest
julia> A = [0 -1 -1; 2 -1.399.. -0.001 0; 1 0.5 -1]
3×3 Matrix{Interval{Float64}}:
 [0, 0]  [-1, -1]                       [-1, -1]
 [2, 2]       [-1.39901, -0.000999999]    [0, 0]
 [1, 1]        [0.5, 0.5]               [-1, -1]

julia> eigenbox(A)
[-1.90679, 0.970154] + [-2.51903, 2.51903]im

julia> eigenbox(A, Hertz())
[-1.64732, 0.520456] + [-2.1112, 2.1112]im
```
