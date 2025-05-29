```
train!(loss, Duplicated(model), data, opt_state)
```

このメソッドは、勾配を計算するためにZygote.jlの代わりにEnzyme.jlを使用しますが、その他は`train!(loss, model, data, opt_state)`と同じです。

Enzymeがロードされているときのみ利用可能です。

!!! compat "New"
    このメソッドはFlux 0.13.9で追加されました。

