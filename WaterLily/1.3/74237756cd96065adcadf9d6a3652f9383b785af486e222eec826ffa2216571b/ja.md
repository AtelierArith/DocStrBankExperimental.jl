```
mult!(p::Poisson,x)
```

ポアソン行列-ベクトル乗算の効率的な関数。ゴーストセルには0を入れて `p.z = p.A x` を填充します。
