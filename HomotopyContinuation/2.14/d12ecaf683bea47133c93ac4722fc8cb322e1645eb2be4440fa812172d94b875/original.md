```
GroupActions(actions::Function...)
```

Store a bunch of group actions `(f1, f2, f3, ...)`. Each action has to return a tuple. The actions are applied in the following sense

1. f1 is applied on the original solution `s`
2. f2 is applied on `s` and the results of 1
3. f3 is applied on `s` and the results of 1) and 2)

and so on

## Example

```julia-repl
julia> f1(s) = (s * s,);

julia> f2(s) = (2s, -s, 5s);

julia> f3(s) = (s + 1,);

julia> GroupActions(f1)(3)
(3, 9)

julia> GroupActions(f1, f2)(3)
(3, 9, 6, -3, 15, 18, -9, 45)

julia> GroupActions(f1,f2, f3)(3)
(3, 9, 6, -3, 15, 18, -9, 45, 4, 10, 7, -2, 16, 19, -8, 46)
```
