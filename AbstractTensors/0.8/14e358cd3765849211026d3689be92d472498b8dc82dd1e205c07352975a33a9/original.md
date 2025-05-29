```
@co fun(args...)
```

Use the macro `@co` to make a pseudoscalar `complement` variant of any functions:

```Julia
julia> @co myfun(x)
comyfun (generic function with 1 method)
```

Now `comyfun(x) = complementleft(myfun(complementright(x)))` is defined.

```Julia
julia> @co myproduct(a,b)
comyproduct (generic function with 1 method)
```

Now `comyproduct(a,b) = complementleft(myproduct(!a,!b))` is defined.
