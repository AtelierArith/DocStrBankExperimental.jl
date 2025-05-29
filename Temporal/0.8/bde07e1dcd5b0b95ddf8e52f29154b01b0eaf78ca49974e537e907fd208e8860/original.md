```
merge(x::TS,y::TS;join::Char='o')::TS
```

Merge two time series objects together by index with an optionally specified join type parameter.

...

# Arguments

  * `x::TS`: Left side of the join.
  * `y::TS`: Right side of the join.

Optional args:

  * `join::Char='o'::TS`: Specifies the logic used to perform the merge, and may take on the values 'o' (outer join), 'i' (inner join), 'l' (left join), or 'r' (right join). Defaults to outer join, whose result is the same as `hcat(x, y)` or `[x y]`.

...
