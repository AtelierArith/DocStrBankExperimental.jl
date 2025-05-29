```
z1 ∧ z2
and(z1,...,zn)
and([z1,...,zn])
```

二つ以上の変数の論理ANDを返します。ベクトル値および行列値のブール式にはドットブロードキャスティングを使用してください。

```julia
@satvariable(z1[1:n], Bool)
@satvariable(z2[n, 1:m], Bool)
z1 .∧ z2
and.(z1, z2) # z1 .∧ z2 と同等
```

特別なケース：

  * `and(z)` は `z` を返します。
  * `and(z, false)` は `false` を返します。
  * `and(z, true)` は `z` を返します。
