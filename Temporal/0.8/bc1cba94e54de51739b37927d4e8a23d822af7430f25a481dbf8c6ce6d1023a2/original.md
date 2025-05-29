```
ijoin(x::TS,y::TS)::TS
```

Inner join two TS objects by index.

Equivalent to `x` INNER JOIN `y` on `x.index` = `y.index`.

...

# Arguments

  * `x::TS`: Left side of the join.
  * `y::TS`: Right side of the join.

...
