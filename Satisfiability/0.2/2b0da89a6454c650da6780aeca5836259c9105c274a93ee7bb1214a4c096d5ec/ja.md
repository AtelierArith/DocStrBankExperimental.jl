```
a > b
a > 0
```

ブール式 a > b を返します。ベクトル値および行列値の式にはドットブロードキャスティングを使用します。

```julia
@satvariable(a[1:n], Int)
@satvariable(b[1:n, 1:m], Int)
a .> b
@satvariable(z, Bool)
a .> z
```
