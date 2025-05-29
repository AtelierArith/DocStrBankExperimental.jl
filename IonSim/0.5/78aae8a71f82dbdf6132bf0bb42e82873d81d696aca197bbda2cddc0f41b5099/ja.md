```
destroy(v::VibrationalMode)
```

`v`のための消滅演算子を返します。次のようになります: `destroy(v) * v[i] = √i * v[i-1]`.
