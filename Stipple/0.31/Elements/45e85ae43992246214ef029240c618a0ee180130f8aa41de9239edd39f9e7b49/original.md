```
@jsexpr(expr)
```

Generates a JS expression from a Julia expression. This is useful for creating Vue.js expressions that need to be passed as strings. They are rendered by `json()` as unmodified text, exactly like `JSONText`.

### Example

```julia julia> @jsexpr(:a + :b) JSExpr("(a + b)")
