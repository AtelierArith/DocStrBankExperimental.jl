```
 subsystem_differential(subsystem, input, t)
```

この関数にメソッドを追加して、時刻 `t` における特定のサブシステムの導関数を記述します。これは `Subsystem{T}` を受け取り、各要素がその要素に関するサブシステムの導関数に対応する `SubsystemStates{T}` を返す必要があります。`input` 引数は、システムグラフ内で `subsystem` に接続されているすべてのサブシステムからの `combine` された入力の合計となります。
