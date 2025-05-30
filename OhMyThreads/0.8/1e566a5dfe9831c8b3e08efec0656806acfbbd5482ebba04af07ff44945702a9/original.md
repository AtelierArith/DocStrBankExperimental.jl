@localize args... expr

Writing

```
@localize x y z expr
```

is equivalent to writing

```
let x=x, y=y, z=z
    expr
end
```

This is useful for avoiding the boxing of captured variables when working with closures.

See https://juliafolds2.github.io/OhMyThreads.jl/stable/literate/boxing/boxing/ for more information about boxed variables.
