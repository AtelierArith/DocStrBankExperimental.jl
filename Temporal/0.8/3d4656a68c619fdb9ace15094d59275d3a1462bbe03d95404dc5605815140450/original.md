```
ojoin(x::TS,y::TS)::TS
```

Outer join two TS objects by index.

Equivalent to `x` OUTER JOIN `y` ON `x.index` = `y.index`.

...

# Arguments

  * `x::TS`: Left side of the join.
  * `y::TS`: Right side of the join.

...
