```
wait!(clk, cond)
```

Delay (suspend) a process on a clock clk until a condition has become true.

# Arguments

  * `clk::Clock`,
  * `cond<:Action`: a condition, true if all expressions or functions therein return true.
