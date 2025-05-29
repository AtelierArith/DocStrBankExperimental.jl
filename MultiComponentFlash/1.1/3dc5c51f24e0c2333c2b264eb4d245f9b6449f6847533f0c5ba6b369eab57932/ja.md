```
phase_saturations(eos, p, T, flashed_mixture)
```

フラッシュされた二相混合物の相飽和を計算します。

混合物が単相であっても、常に (S*l, S*v) の名前付きタプルを返します。

存在しない相の値はゼロになります。
