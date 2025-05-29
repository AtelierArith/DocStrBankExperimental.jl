```
@buffer(specs, ex)
```

Create a [`MAllocBuffer`](@ref) object with the given specifications `specs`  and execute the expression `ex` with the buffer.

The `specs` have the following format:

  * `buf(100)` creates a buffer `buf` of type `Float64` with length `100`.
  * `buf(Int, 100)` creates a buffer `buf` of type `Int` with length `100`.

The buffer is freed after the expression is executed.

# Example

```julia
@buffer buf(Float64, 300) begin
  A = alloc!(buf, 10, 10)
  B = alloc!(buf, 10, 10)
  C = alloc!(buf, 10, 10)
  rand!(A)
  rand!(B)
  @tensor C[i,j] = A[i,l] * B[l,j]
end
```
