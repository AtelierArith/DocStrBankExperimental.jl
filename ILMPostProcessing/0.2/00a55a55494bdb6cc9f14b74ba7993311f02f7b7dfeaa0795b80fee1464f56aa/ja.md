```
dmd(Xfull,r)
```

`Xfull`の拡張スナップショットデータから最初の`r` DMDモードを計算します。元のデータとシフトされたデータは`Xfull`から取得されます。すなわち、`X = Xfull[1:m-1]`および`Xp = Xfull[2:m]`です。

これにより、`modes`および`evals`フィールドを持つ`DMDModes`構造体にDMDモードとDMD固有値が返されます。
