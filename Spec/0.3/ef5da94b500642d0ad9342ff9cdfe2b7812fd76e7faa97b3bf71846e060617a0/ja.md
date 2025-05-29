`specapply(f, args...)`

`f(args...)`を評価し、遭遇したすべての関数の前提条件と後提条件をチェックします。

```
f(x) = abs(x)
@post f(ret, x) = x > 0)
specapply(f, 0.3)
```
