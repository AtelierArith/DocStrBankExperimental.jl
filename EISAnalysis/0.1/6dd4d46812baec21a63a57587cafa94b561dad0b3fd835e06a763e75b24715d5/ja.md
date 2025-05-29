```
initialize()
```

回路を構築する際の使いやすさのために、すべての回路要素を生成します。

次の変数があなたの環境に追加されます     r = Resistor()     c = Capacitor()     l = Inductor()     q = CPE()     wo = Warburg("open")     ws = Warburg("short") ここから、オーバーロードされた * および ^ 演算子を使用して、回路を迅速に構築し、パラメータを直接調整できます。

# 例

```julia
using EISAnalysis
eval(initialize())
print(r.R)

# 出力

1.0
```
