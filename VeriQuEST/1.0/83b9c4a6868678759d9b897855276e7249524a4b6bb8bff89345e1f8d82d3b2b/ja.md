```
initialise_qubit(qubit::Union{ComputationQubit,TrapQubit}, input::Union{InputQubits,InputQubits,NoInputQubits}, quantum_state, qubit_index, qubit_input_value::Float64)
```

この関数は、入力値によって決定される位相を持つ量子状態でキュービットを初期化します。入力値が浮動小数点数の場合、入力値を位相として持つ重ね合わせ状態にキュービットを初期化します。入力値が浮動小数点数でない場合、`QubitFloatPhaseInitialisationError`をスローします。

# 引数

  * `qubit::Union{ComputationQubit,TrapQubit}`: キュービットのタイプ。
  * `input::Union{InputQubits,InputQubits,NoInputQubits}`: 入力オブジェクト。
  * `quantum_state`: キュービットを含む量子状態。
  * `qubit_index`: 量子状態におけるキュービットのインデックス。
  * `qubit_input_value::Float64`: キュービットの入力値で、位相を決定します。

# 例

```julia
qubit = ComputationQubit()
input = InputQubits()
quantum_state = createQureg(1, env)
qubit_index = 1
qubit_input_value = 0.5
initialise_qubit(qubit, input, quantum_state, qubit_index, qubit_input_value)
```
