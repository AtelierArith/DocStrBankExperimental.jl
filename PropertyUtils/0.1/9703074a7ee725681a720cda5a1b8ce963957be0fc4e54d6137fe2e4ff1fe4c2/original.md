```
@with src expr
```

  * For every symbol `x` in `expr`, replace it with `hasproperty(src, x) ? src.x : x`.
  * use `identity` to leave an identifier untouched.

# Example

```
x = 3
nt = (x = 1, y = 2)
@with nt x + y + identity(x)  # 6
```
