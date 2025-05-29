```
@print(items...)
```

This is a unified print statement.

# Platform differences

  * `GPU`: This will reorganize the items to print via `@cuprintf`
  * `CPU`: This will call `print(items...)`
