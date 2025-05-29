```
SimulatorObservable{N,outputType<:SimulatorOutput,funcType,coordsType} <: Observable{outputType}
```

シミュレーターからの出力を格納する名前付き「オブザーバブル」を表します。 `obsfunc` はシミュレーターの状態から観測量へのマッピングを定義します。 `output` の型と実装は、サンプルがどのように格納されるかを決定します。 最も単純な出力型は `Transient` で、これは単に最後に観測された出力へのポインタを保持します。
