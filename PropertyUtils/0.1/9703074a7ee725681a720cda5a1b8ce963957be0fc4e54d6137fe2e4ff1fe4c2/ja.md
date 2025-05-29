```
@with src expr
```

  * `expr`内のすべてのシンボル`x`を`hasproperty(src, x) ? src.x : x`で置き換えます。
  * 識別子をそのままにするために`identity`を使用します。

# 例

```
x = 3
nt = (x = 1, y = 2)
@with nt x + y + identity(x)  # 6
```
