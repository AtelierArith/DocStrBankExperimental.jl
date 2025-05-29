```
find_main_equation(model, var)
```

Return the name of the first equation that matches the pattern `var[t] = __`. If such equation does not exist, return the name of the first equation that contains `var[t]` anywhere in its expression. If that doesn't exist either, return `nothing`.
