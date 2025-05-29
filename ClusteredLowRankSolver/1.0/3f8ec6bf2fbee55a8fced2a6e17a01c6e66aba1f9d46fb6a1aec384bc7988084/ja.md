```
find_field(primalsol, dualsol, max_degree=4; valbound=1e-15, errbound=1e-15, bits=100, max_coeff=1000)
```

ヒューリスティックにカーネルが定義される可能性のある体を見つけます。

絶対値が少なくとも `valbound` である値のみを考慮します。選択されたエントリが誤差境界 `errbound` でおおよそ生成子であるような最小多項式を見つけます。`bits` ビット数を使用し、最大係数が `max_coeff` を超える最小多項式は拒否します。
