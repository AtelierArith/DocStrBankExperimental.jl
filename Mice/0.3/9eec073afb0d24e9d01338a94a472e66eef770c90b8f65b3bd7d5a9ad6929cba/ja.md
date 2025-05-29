```
with(
    mids::Mids,
    func::Function
    )
```

重複して分析を行う多重インプットデータセット（`Mids`）を実施します。

この関数は2つの引数を取ります。まず最初に`Mids`オブジェクト自体、次に関数（`func`）です。この関数は`data -> analysisFunction(arguments, data, moreArguments...)`の形を取る必要があります。ここで`data`は関数内のデータ引数の位置を表します。

例えば：`with(mids, data -> lm(@formula(y ~ x1 + x2), data))`
