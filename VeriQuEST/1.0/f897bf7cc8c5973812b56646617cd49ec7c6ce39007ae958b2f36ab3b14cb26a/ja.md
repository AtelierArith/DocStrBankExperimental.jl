```
initialise_qubit(mbqc::MBQC, qubit::Union{ComputationQubit,TrapQubit}, input::Union{InputQubits,InputQubits,NoInputQubits}, quantum_state, qubit_index)
```

この関数は、位相を追加せずに量子状態のキュービットを重ね合わせ状態に初期化します。キュービットにアダマールゲートを適用し、重ね合わせ状態にします。

# 引数

  * `mbqc::MBQC`: MBQCオブジェクト。
  * `qubit::Union{ComputationQubit,TrapQubit}`: キュービットのタイプ。
  * `input::Union{InputQubits,InputQubits,NoInputQubits}`: 入力オブジェクト。
  * `quantum_state`: キュービットを含む量子状態。
  * `qubit_index`: 量子状態におけるキュービットのインデックス。

# 例

```julia
mbqc = MBQC()
qubit = ComputationQubit()
input = InputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
initialise_qubit(mbqc, qubit, input, quantum_state, qubit_index)
```
