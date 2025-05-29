```
@print_buffer_usage(buf, ex)
```

Print buffer `buf` usage in expression `ex`.

The macro generates a body of a function that calculates the length of buffer `buf`  in expression `ex`. It is possible to use the macro with multiple buffers, e.g.,  `@print_buffer_usage buf1 buf2 begin ... end`.

All function calls with `buf` as an argument are replaced with `pseudo_<function>` calls. `pseudo_alloc!`,`pseudo_drop!`, and `pseudo_reset!` functions are pre-defined, custom `pseudo_`functions can be defined if necessary.

# Example

```julia buf = Buffer(100000) @print*buffer*usage buf begin if true   A = alloc!(buf, 10, 10, 20) else   A = alloc!(buf, 10, 10, 30) end B = alloc!(buf, 10, 10, 10) if true   C = alloc!(buf, 10, 20) else   C = alloc!(buf, 10, 30) end rand!(B) rand!(C) An = neuralyze(A) @tensor An[i,j,k] = B[i,j,l] * C[l,k] drop!(buf, B, C) reset!(buf) end
