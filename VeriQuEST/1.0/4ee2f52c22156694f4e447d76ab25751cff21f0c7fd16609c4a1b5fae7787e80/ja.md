```
init_qubit(::DummyQubit)::Int64
```

この関数はメタグラフ内のキュービットを初期化するために使用されます。状態は指定されていませんが、ダミーキュービットの初期状態のビットが返されます。

# 引数

  * `dummy::DummyQubit`: DummyQubitオブジェクト。

# 戻り値

  * ダミーキュービットの初期状態のビットを表すInt64。

# 例

`julia dummy = DummyQubit() bit = init_qubit(dummy)``
