```
phaseDAC!(rpc::RedPitayaCluster, chan::Integer, component::Integer, value)
```

単一のRedPitayaと同様に、`chan`インデックスはクラスター内で利用可能な合計チャネルを指し、各`RedPitaya`につき2つです。例えば、チャネル`4`は2番目の`RedPitaya`の2番目のチャネルを指します。
