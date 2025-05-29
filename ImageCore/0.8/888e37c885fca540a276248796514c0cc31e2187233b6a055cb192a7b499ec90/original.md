```
StackedView(B, C, ...) -> A
```

Present arrays `B`, `C`, etc, as if they are separate channels along the first dimension of `A`. In particular,

```
B == A[1,:,:...]
C == A[2,:,:...]
```

and so on. Combined with `colorview`, this allows one to combine two or more grayscale images into a single color image.

See also: [`colorview`](@ref).
