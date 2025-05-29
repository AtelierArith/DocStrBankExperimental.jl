```
z1 ∨ z2
or(z1,...,zn)
or([z1,...,zn])
```

2つ以上の変数の論理和を返します。ベクトル値および行列値のブール式にはドットブロードキャスティングを使用してください。

```julia
@satvariable(z1[1:n], Bool)
@satvariable(z2[1:m, 1:n], Bool)
z1 .∨ z2
or.(z1, z2) # z1 .∨ z2 と同等
```

特別なケース：

  * `or(z)` は `z` を返します。
  * `or(z, false)` は `z` を返します。
  * `or(z, true)` は `true` を返します。

**注意： ∨ (`\vee`) は ASCII 文字の v ではありません。**
