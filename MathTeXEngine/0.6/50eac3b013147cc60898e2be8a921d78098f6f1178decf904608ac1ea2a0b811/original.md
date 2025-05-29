```
texparse(tex::String ; showdebug=false)
```

Parse a string representing a single LaTeX expression into nested TeXExpr.

See the documentation for the possible combinations of expression head and arguments.

Setting `showdebug` to `true` show a very verbose break down of the parsing.
