```
support_enumeration_task(c, g)
```

Task version of `support_enumeration`.

# Arguments

  * `c::Channel`: Channel to be binded with the support enumeration task.
  * `g::NormalFormGame{2}`: 2-player NormalFormGame instance.

# Returns

  * `::Task`: Runnable task for generating Nash equilibria.
