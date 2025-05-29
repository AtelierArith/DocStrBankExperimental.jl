```
joinprops(items...)
```

Join items into a single struct with shared properties.  The first item that has the requested property will be used.

# Example

```
a = (x = 1, y = 2)
b = (x = 3, z = 4)
j = joinprops(a,b)
j.x == 1
j.z == 4
```
