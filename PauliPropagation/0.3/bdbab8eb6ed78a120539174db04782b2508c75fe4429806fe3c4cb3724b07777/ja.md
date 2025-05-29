```
staircasetopology(nqubits::Integer; periodic=false)
```

`nqubits`量子ビット上に1D階段トポロジーを作成します。量子ビットは階段状に接続されており、量子ビット`i`は量子ビット`i+1`に接続されています。`periodic`が`true`に設定されている場合、最後の量子ビットは最初の量子ビットに接続されます。
