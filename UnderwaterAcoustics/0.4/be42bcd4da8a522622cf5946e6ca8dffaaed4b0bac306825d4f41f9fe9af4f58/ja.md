```
acoustic_field(pm::PekerisRayTracer, tx, rxs; mode=:coherent)
```

受信機 `rxs` における音響場を、送信機 `tx` によって Pekeris 波導内で計算します。`mode=:incoherent` の場合、場は非コヒーレントに計算されます。それ以外の場合、場はコヒーレントに計算されます。
