```
coinflip(labels::Vector{Bool})
```

与えられたラベルのベクトルに対して、スキルのない分類器の混同行列を返します。予測はランダムに行われ、各クラスは1/2の確率で選択されます。
