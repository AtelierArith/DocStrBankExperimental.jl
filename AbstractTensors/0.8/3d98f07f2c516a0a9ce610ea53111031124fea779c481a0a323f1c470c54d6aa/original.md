```
@pseudo fun(args...)
```

Use the macro `@pseudo` to make a pseudoscalar `complement` variant of any functions:

```Julia
julia> @pseudo myfun(x)
pseudomyfun (generic function with 1 method)
```

Now `pseudomyfun(x) = complementleft(myfun(complementright(x)))` is defined.

```Julia
julia> @pseudo myproduct(a,b)
pseudomyproduct (generic function with 1 method)
```

Now `pseudomyproduct(a,b) = complementleft(myproduct(!a,!b))` is defined.
