```
GreedyMethod{MT}
GreedyMethod(; α = 0.0, temperature = 0.0, nrepeat=1)
```

高速だが性能が悪い貪欲最適化手法。入力引数は次の通りです。

```
* `α` は損失関数のパラメータで、ペアワイズ相互作用の場合、L = size(out) - α * (size(in1) + size(in2))
* `temperature` はサンプリングのパラメータで、ゼロの場合は最小損失が選択されます。ゼロ以外の場合は、ボルツマン分布により損失が選択され、p ~ exp(-loss/temperature) で与えられます。
* `nrepeat` は繰り返しの回数で、最良の収縮順序を返します。
```
