```
acoustic_field(pm::PekerisModeSolver, tx, rxs; mode=:coherent)
```

受信機 `rxs` における音響場を、ペケリス波導における送信機 `tx` によって計算します。`mode=:incoherent` の場合、場は非コヒーレントに計算できます。それ以外の場合、場はコヒーレントに計算されます。
