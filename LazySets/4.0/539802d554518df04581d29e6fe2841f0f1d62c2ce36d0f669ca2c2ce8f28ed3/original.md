```
isempty(C::Complement)
```

Check whether the complement of a set is empty.

### Input

  * `C` – complement of a set

### Output

`false` unless the original set is universal.

### Algorithm

We use the `isuniversal` function.
