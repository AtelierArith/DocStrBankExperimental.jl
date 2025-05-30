```
Thunk(()->v)
```

A thunk is a deferred computation. It wraps a zero argument closure that when invoked returns a tangent. `@thunk(v)` is a macro that expands into `Thunk(()->v)`.

To evaluate the wrapped closure, call [`unthunk`](@ref) which is a no-op when the argument is not a `Thunk`.

```jldoctest
julia> t = @thunk(3)
Thunk(var"#4#5"())

julia> unthunk(t)
3
```

### When to `@thunk`?

When writing `rrule`s (and to a lesser exent `frule`s), it is important to `@thunk` appropriately. Propagation rules that return multiple derivatives may not have all deriviatives used.  By `@thunk`ing the work required for each derivative, they then compute only what is needed.

#### How do thunks prevent work?

If we have `res = pullback(...) = @thunk(f(x)), @thunk(g(x))` then if we did `dx + res[1]` then only `f(x)` would be evaluated, not `g(x)`. Also if we did `ZeroTangent() * res[1]` then the result would be `ZeroTangent()` and `f(x)` would not be evaluated.

#### So why not thunk everything?

`@thunk` creates a closure over the expression, which (effectively) creates a `struct` with a field for each variable used in the expression, and call overloaded.

Do not use `@thunk` if this would be equal or more work than actually evaluating the expression itself. This is commonly the case for scalar operators.

For more details see the manual section [on using thunks effectively](https://juliadiff.org/ChainRulesCore.jl/dev/rule_author/writing_good_rules.html#Use-Thunks-appropriately).
