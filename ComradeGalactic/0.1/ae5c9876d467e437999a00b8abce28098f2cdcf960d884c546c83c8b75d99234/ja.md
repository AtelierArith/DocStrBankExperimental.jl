```
`laplace(prob, opt, args...; kwargs...)`
```

確率または事後のラプラスまたは二次近似を計算します。`args` と `kwargs` は GalacticOptim.solve 関数に渡されます。

二次近似は通常のパラメータ空間ではなく、変換された事後の空間で行われることに注意してください。これは、境界に直面する可能性がある制約付き問題にとってより良いものです。
