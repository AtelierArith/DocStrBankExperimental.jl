```
codetransform!(tr, dst, src)
```

Apply a code transformation function `tr` on the methods of a function `src`, adding the transformed methods to another function `dst`.

Example: Search-and-replace a constant in a function.

```
g(x) = x + 13
function e end
codetransform!(g => e) do ci
    for ex in ci.code
        if ex isa Expr
            map!(x -> x === 13 ? 7 : x, ex.args, ex.args)
        end
    end
    ci
end
e(1) # returns 8
```
