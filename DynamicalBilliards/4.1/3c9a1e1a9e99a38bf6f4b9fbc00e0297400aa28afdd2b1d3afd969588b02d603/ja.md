```
propagate!(p::AbstractParticle, t)
```

与えられた時間`t`に対して粒子`p`を伝播させ、適切に`p.pos`および`p.vel`フィールドを変更します。

```
propagate!(p, position, t)
```

同様のことを行いますが、粒子が到達すべきすでに計算された`position`を利用します。
