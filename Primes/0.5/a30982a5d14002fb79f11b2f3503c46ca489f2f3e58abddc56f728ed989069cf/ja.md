```
eachfactor(n::Integer)->FactorIterator
```

`n`の因数を`(因数, 重複度)`のペアで遅延イテレータとして返します。これは、特に小さな数（例：`>2^16`の因数を持たない数）の場合、`factor(n)`に必要なストレージを割り当てることが大きなオーバーヘッドを引き起こす可能性があるため、乗法関数を計算するのに非常に便利です。
