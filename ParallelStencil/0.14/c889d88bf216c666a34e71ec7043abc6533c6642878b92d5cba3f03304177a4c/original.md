```
@∀ x ∈ X statement
@∀ x in X statement
@∀ x = X statement
```

Expand the `statement` for all `x` in `X`.

# Arguments

  * `x`: the name of the variable the `statement` is to be expanded with.
  * `X`: the set of names or range of values `x` is to be expanded over.
  * `statement`: the statement to be expanded.

# Examples

```
@∀ i ∈ (x,z) @all(C.i) = @all(A.i) + @all(B.i)                     # Equivalent to: @all(C.x) = @all(A.x) + @all(B.x)
                                                                   #                @all(C.z) = @all(A.z) + @all(B.z)

@∀ i ∈ (y,z) C.i[ix,iy,iz] = A.i[ix,iy,iz] + B.i[ix,iy,iz]         # Equivalent to: C.y[ix,iy,iz] = A.y[ix,iy,iz] + B.y[ix,iy,iz]
                                                                   #                C.z[ix,iy,iz] = A.z[ix,iy,iz] + B.z[ix,iy,iz]

@∀ (ij,i,j) ∈ ((xy,x,y), (xz,x,z), (yz,y,z)) @all(C.ij) = @all(A.i) + @all(B.j)  # Equivalent to: @all(C.xy) = @all(A.x) + @all(B.y)
                                                                                 #                @all(C.xz) = @all(A.x) + @all(B.z)
                                                                                 #                @all(C.yz) = @all(A.y) + @all(B.z)

@∀ i ∈ 1:N @all(C[i]) = @all(A[i]) + @all(B[i])                    # Equivalent to: @all(C[1]) = @all(A[1]) + @all(B[1])
                                                                   #                @all(C[2]) = @all(A[2]) + @all(B[2])
                                                                   #                ...
                                                                   #                @all(C[N]) = @all(A[N]) + @all(B[N])

@∀ i ∈ 1:N C[i][ix,iy,iz] = A[i][ix,iy,iz] + B[i][ix,iy,iz]        # Equivalent to: C[1][ix,iy,iz] = A[1][ix,iy,iz] + B[1][ix,iy,iz]
                                                                   #                C[2][ix,iy,iz] = A[2][ix,iy,iz] + B[2][ix,iy,iz]
                                                                   #                ...
                                                                   #                C[N][ix,iy,iz] = A[N][ix,iy,iz] + B[N][ix,iy,iz]
```

!!! note "Performance note"
    Besides enabling a concise notation for certain sets of equations, the `@∀` macro is also designed to replace for loops over a small range of values in compute kernels, leading often to better performance.


!!! note "Symbol ∀"
    The symbol `∀` can be obtained, e.g., in the Julia REPL or VSCode, by typing `orall` and pressing `TAB`.

