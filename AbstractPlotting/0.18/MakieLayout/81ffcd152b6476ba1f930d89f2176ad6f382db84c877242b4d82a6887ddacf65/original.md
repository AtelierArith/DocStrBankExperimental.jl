```
reset_limits!(ax; xauto = true, yauto = true)
```

Resets the axis limits depending on the value of `ax.limits`. If one of the two components of limits is nothing, that value is either copied from the targetlimits if `xauto` or `yauto` is true, respectively, or it is determined automatically from the plots in the axis. If one of the components is a tuple of two numbers, those are used directly.
