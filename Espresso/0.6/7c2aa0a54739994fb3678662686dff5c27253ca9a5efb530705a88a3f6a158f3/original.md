Removes unused variables from multiline expressions, e.g. in:

```
x = u * v
y = x + 1
z = 2x
```

`y` isn't used to compute output variable `z`, so it's removed:

```
x = u * v
z = 2x
```
