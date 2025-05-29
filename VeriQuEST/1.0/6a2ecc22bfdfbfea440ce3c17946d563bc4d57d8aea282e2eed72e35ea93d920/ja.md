```
initialise_qubit(dummy::DummyQubit, noinput::NoInputQubits, quantum_state, qubit_index, qubit_input_value::Int)
```

この関数は量子状態においてキュービットを初期化します。キュービットの入力値がゼロの場合、何もしません。入力値が1の場合、キュービットにパウリ-Xゲートを適用します。入力値がゼロでも1でもない場合、`DummyQubitZeroOneInitialisationError`をスローします。

# 引数

  * `dummy::DummyQubit`: DummyQubitオブジェクト。
  * `noinput::NoInputQubits`: NoInputQubitsオブジェクト。
  * `quantum_state`: キュービットを含む量子状態。
  * `qubit_index`: 量子状態におけるキュービットのインデックス。
  * `qubit_input_value::Int`: キュービットの入力値。

# 例

```julia
dummy = DummyQubit()
noinput = NoInputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
qubit_input_value = 0
initialise_qubit(dummy, noinput, quantum_state, qubit_index, qubit_input_value)
```
