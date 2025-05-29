```
symeval(expr::Any)
```

send `expr` through the Symata evaluation sequence. `expr` is an `Mxpr` or number, symbol, etc.

In particular, an `Expr` (i.e. not translated to Symata) Symata-evaluated (whic in this case means returned unchanged) by the Symata evaluation sequence.
