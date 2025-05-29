```
manual_texexpr(data)
```

Convenience function to manually create a TeXExpr from tuples or latex strings.

# Example

julia> manual_texexpr((:expr, 'a', (:spaced, '+'), raw"\omega^2")) TeXExpr :expr ├─ 'a' ├─ TeXExpr :spaced │  └─ '+' └─ TeXExpr :decorated    ├─ TeXExpr :symbol    │  ├─ 'ω'    │  └─ "\omega"    ├─ nothing    └─ '2' ```
