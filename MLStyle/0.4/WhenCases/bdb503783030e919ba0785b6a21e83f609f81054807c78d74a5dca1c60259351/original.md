1. Allow destructuring in binding sequences of `let` syntax.

In binding sequences,

  * For bindings in form of `a = b` and `f(x) = y`, it's regarded as pattern matching here.
  * For others like `@inline f(x) = 1`, it's the same as the original let binding(not pattern matching).

```julia
    @when let (a, 1) = x,
          [b, c, 5] = y
        (a, b, c)
    end
```

2. For a regular assignment, like

```julia
    @when (a, 2) = x begin
        # dosomething
    end
```

It's nothing different from

```julia
    @match x begin
        (a, 2) => # dosomething
        _ => nothing
    end
```

3. For multiple branches, we can have

```julia
x = 1
@when let (_, _) = x
    :tuple
@when begin ::Float64 = x end
    :float
@when ::Int = x
    :int
@otherwise
    :unknown
end
```

4. Also, you can use predicates when matching, in the form

of `cond.?` or `if cond end`:

```julia
x = 1
y = (1, 2)
cond1 = true
cond2 = true
@when let cond1.?,
          (a, b) = x
    a + b
@when begin if cond2 end
            (a, b) = y
      end
    a + b
end
```
