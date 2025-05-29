```
pywith(f, o, d=nothing)
```

Pythonにおける `with o as x: f(x)` に相当し、ここで `x` は `Py` です。

成功した場合、`f(x)` の値が返されます。

例外が発生したが抑制された場合は、`d` が返されます。
