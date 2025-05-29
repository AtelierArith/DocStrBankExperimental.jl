```
warn_on_boundary(ho, sense = :min)
```

Prints a warning message for each parameter where the optimum was obtained on an extreme point of the sampled space.

Example: If parameter `a` can take values in 1:10 and the optimum was obtained at `a = 1`, it's an indication that the parameter was constraind by the search space. The warning is effective even if the lowest value of `a` that was sampled was higher than 1, but the optimum occured on the lowest sampled value.
