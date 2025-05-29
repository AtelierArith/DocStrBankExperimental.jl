```
manual_texexpr(data)
```

タプルまたはLaTeX文字列からTeXExprを手動で作成するための便利な関数です。

# 例

julia> manual_texexpr((:expr, 'a', (:spaced, '+'), raw"\omega^2")) TeXExpr :expr ├─ 'a' ├─ TeXExpr :spaced │  └─ '+' └─ TeXExpr :decorated    ├─ TeXExpr :symbol    │  ├─ 'ω'    │  └─ "\omega"    ├─ nothing    └─ '2' ```
