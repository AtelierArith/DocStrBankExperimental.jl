```
degree(t::AbstractTermLike)
```

項 `t` の単項式の *総次数* を返します。すなわち、`sum(exponents(t))` です。

```
degree(t::AbstractTermLike, v::AbstractVariable)
```

項 `t` の単項式における変数 `v` の指数を返します。

### 例

`degree(x^2*y)` を呼び出すと 3 が返されます。これは $2 + 1$ です。`degree(x^2*y, x)` を呼び出すと 2 が返され、`degree(x^2*y, y)` を呼び出すと 1 が返されます。
