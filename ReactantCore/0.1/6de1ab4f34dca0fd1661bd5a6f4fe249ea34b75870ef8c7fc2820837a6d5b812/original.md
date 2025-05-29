```
@trace <expr>
```

Converts certain expressions like control flow into a Reactant friendly form. Importantly, if no traced value is found inside the expression, then there is no overhead.

## Currently Supported

  * `if` conditions (with `elseif` and other niceties) (`@trace if ...`)
  * `if` statements with a preceeding assignment (`@trace a = if ...`) (note the positioning of the macro needs to be before the assignment and not before the `if`)
  * `for` statements with a single induction variable iterating over a syntactic `StepRange` of integers.

## Special Considerations

  * Apply `@trace` only at the outermost `if`. Nested `if` statements will be automatically expanded into the correct form.

# Extended Help

## Caveats (Deviations from Core Julia Semantics)

### New variables introduced

```julia
@trace if x > 0
    y = x + 1
    p = 1
else
    y = x - 1
end
```

In the outer scope `p` is not defined if `x ≤ 0`. However, for the traced version, it is defined and set to a dummy value.

### Short Circuiting Operations

```julia
@trace if x > 0 && z > 0
    y = x + 1
else
    y = x - 1
end
```

`&&` and `||` are short circuiting operations. In the traced version, we replace them with `&` and `|` respectively.

### Type-Unstable Branches

```julia
@trace if x > 0
    y = 1.0f0
else
    y = 1.0
end
```

This will not compile since `y` is a `Float32` in one branch and a `Float64` in the other. You need to ensure that all branches have the same type.

Another example is the following for loop which changes the type of `x` between iterations.

```julia
x = ... # ConcreteRArray{Int64, 1}
for i in 1f0:0.5f0:10f0
    x = x .+ i # ConcreteRArray{Float32, 1}
end
```

### Certain Symbols are Reserved

Symbols like [:(:), :nothing, :missing, :Inf, :Inf16, :Inf32, :Inf64, :Base, :Core] are not allowed as variables in `@trace` expressions. While certain cases might work but these are not guaranteed to work. For example, the following will not work:

```julia
function fn(x)
    nothing = sum(x)
    @trace if nothing > 0
        y = 1.0
    else
        y = 2.0
    end
    return y, nothing
end
```
