```
s = buffer(input; buf_size = Inf, timespan = 1, type_stable = false)
```

信号を作成し、`input`への更新を最大サイズの`buf_size`まで、または`timespan`秒が経過するまでバッファリングします。信号の値は、最後に出力された完全なバッファ、またはバッファがこれまでに満たされたことがない場合は空のベクターです。

バッファの型は`Any`になりますが、`type_stable`が`true`に設定されている場合は、最初に遭遇したアイテムの値に設定されます。
