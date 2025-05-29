```
prev(list, state) -> item, prevstate
```

Returns the current item from `list` and sets the state to point to the previous entry. It hold that

```
_, p = prev(list, s)
_, n = next(list, p)
n == s
```
