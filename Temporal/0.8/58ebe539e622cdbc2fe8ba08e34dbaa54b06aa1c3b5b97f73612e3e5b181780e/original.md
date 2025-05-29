```
ljoin(x::TS, y::TS)::TS
```

Left join two TS objects by index.

Equivalent to `x` LEFT JOIN `y` ON `x.index` = `y.index`.

...

# Arguments

  * `x::TS`: Left side of the join.
  * `y::TS`: Right side of the join.

...
