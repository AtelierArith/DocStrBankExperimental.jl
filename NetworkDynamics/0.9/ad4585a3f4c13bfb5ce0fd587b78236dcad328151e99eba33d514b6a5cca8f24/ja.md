```
abstract type Aggregator end
```

アグリゲーターのための抽象スーパタイプ。アグリゲーターはすべてのコンポーネントの出力バッファで動作し、各頂点ごとの集約されたエッジ値で集約バッファを満たします。

すべてのアグリゲーターにはコンストラクタがあります。

```
Aggegator(aggfun)
```

例えば、

```
SequentialAggreator(+)
```
