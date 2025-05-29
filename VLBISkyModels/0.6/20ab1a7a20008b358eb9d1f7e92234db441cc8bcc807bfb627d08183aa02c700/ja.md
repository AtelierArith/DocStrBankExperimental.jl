```
Rotate(ξ)
```

回転したモデルの型。これは回転したモデルのより詳細な制御です。

# 例

```julia-repl
julia> modify(Gaussian(), Rotate(2.0)) == rotated(Gaussian(), 2.0)
true
```
