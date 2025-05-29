```
@SArray [a b; c d]
@SArray [[a, b];[c, d]]
@SArray [i+j for i in 1:2, j in 1:2]
@SArray ones(2, 2, 2)
```

A convenience macro to construct `SArray` with arbitrary dimension. It supports:

1. (typed) array literals.

    !!! note
        Every argument inside the square brackets is treated as a scalar during expansion. Thus `@SArray[a; b]` always forms a `SVector{2}` and `@SArray [a b; c]` always throws an error.
2. comprehensions

    !!! note
        The range of a comprehension is evaluated at global scope by the macro, and must be made of combinations of literal values, functions, or global variables.
3. initialization functions

    !!! note
        Only support `zeros()`, `ones()`, `fill()`, `rand()`, `randn()`, and `randexp()`
