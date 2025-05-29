```
overlapwithcomputational(pstr::PauliString, onebitinds)
```

指定された `onebitinds` で全ての1ビットを持ち、他は0ビットの計算基底状態とのパウリ文字列の重なりを計算します。例えば、`overlapwithcomputational(pstr, [1,2,4])` は `|1101000...>` との重なりを返し、ゼロまたは `pstr.coeff` のプラス/マイナスになります。
