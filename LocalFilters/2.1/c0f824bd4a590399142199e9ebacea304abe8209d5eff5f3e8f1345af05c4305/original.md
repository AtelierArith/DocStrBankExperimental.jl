```
B = reverse_kernel(args...)
```

yields a kernel `B` which is similar to `A = kernel(args...)` but with reversed ordering in the sense that `B[i] == A[-i]` holds for all indices `i` such that `-i` is a valid index in `A`. As a consequence, a correlation by `B` yields the same result as a convolution by `A` and conversely.

See also [`LocalFilters.kernel`](@ref) and [`LocalFilters.strel`](@ref).
