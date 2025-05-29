```
CountMinSketch(T = Number; nhash=50, hashlength=1000, storagetype=Int)
```

`nhash` 個のハッシュ関数と幅 `hashlength` を持つ Count-Min スケッチを作成します。スケッチ内のカウントは `storagetype` として保存されます。

これにより、データストリーム内の値 `x` の出現回数の上限を `value(count_min_sketch, x)` を介して計算できます。詳細と誤差の範囲については、参考文献セクションを参照してください。

# 例

```
o = CountMinSketch()

y = rand(1:100, 10^6)

fit!(o, y)

value(o, 1)

sum(y .== 1)
```

# 参考文献

  * https://florian.github.io/count-min-sketch/
