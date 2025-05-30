```
dtransform(val, fn, workers, tgt::Symbol=val)
```

`workers`で利用可能な`val`としてのワーカー・ローカル分散データを、関数`fn`によってインプレースで変換します。結果を`tgt`に保存します（デフォルトは`val`）。

# 例

```
# 保存されたすべてのデータを2倍にする
dtransform(:myData, (d)->(2*d), workers())
```
