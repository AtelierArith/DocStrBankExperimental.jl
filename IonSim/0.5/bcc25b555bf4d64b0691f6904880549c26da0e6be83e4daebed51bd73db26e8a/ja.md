```
matrixelement(ion, transition::Tuple, laser, chamber::Chamber, time::Real)
```

`matrixelement(ion, transition, I, ϵhat, khat, Bhat)`を呼び出し、`I`、`ϵhat`、および`khat`は`laser`の`time`で評価され、`Bhat`は`chamber`で評価されます。

`ion`は、IonまたはIntのいずれかで、`chamber`内の希望するイオンのインデックスを示します。`laser`は、LaserまたはIntのいずれかで、`chamber`内の希望するレーザーのインデックスを示します。`ion`と`laser`は、両方ともインデックスであるか、またはそれぞれのStructである必要があります。
