```
AbstractGateSymbol
```

`GateSymbol`は`AbstractGateSymbol`のインスタンス化です。これは`Gate` [constuctor](https://docs.julialang.org/en/v1/manual/constructors/)に引数として渡すことができ、`Gate`は`target`量子ビットにも関連付けられています。`QuantumCircuit`に追加されると、`Gate`はその`target_qubits`に配置されます。`AbstractGateSymbol`は、すべての`GateSymbols`を[`get_connected_qubits()`](@ref)のような関数のデフォルト実装にディスパッチするのに役立ちます。これらの関数は、異なる実装を必要とする`GateSymbols`に特化することができます。

`AbstractGateSymbol`は抽象型であり、インスタンス化することはできません。各具体的な`GateSymbols`の型は、`AbstractGateSymbol`のサブタイプである構造体です。`AbstractGateSymbol`の各子孫は、少なくとも以下のメソッドを実装する必要があります：

  * `get_operator(gate::AbstractGateSymbol, T::Type{<:Complex}=ComplexF64})::AbstractOperator`
  * `get_num_connected_qubits(gate::AbstractGateSymbol)::Integer`

# 例

新しい`GateSymbol`型ごとに構造体を定義する必要があります。以下のX_45 `GateSymbol`は、$X$軸の周りに$45°$の回転を適用します：

```jldoctest gate_struct
julia> struct X45 <: AbstractGateSymbol
       end;
```

新しい`GateSymbol`に必要な接続量子ビットの数を定義する必要があります：

```jldoctest gate_struct
julia> Snowflurry.get_num_connected_qubits(::X45) = 1

```

`Gate`コンストラクタは次のように定義する必要があります：

```jldoctest gate_struct
julia> x_45(target::Integer) = Gate(X45(), [target]);
```

デフォルト精度`ComplexF64`の`Operator`コンストラクタも定義する必要があります：

```jldoctest gate_struct
julia> x_45(T::Type{<:Complex} = ComplexF64) = rotation_x(π/4, T);

```

`QuantumCircuit`内でゲートの効果をシミュレートするため、または`Ket`に適用するために、`get_operator`関数を拡張する必要があります：

```jldoctest gate_struct
julia> function Snowflurry.get_operator(gate::X45, T::Type{<:Complex} = ComplexF64)
          return rotation_x(π/4, T)
       end

```

ゲートの逆も`inv`関数を拡張することで指定できます：

```jldoctest gate_struct
julia> Base.inv(::X45) = Snowflurry.RotationX(-π/4);

```

`X_45` `Gate`のインスタンスを作成し、その逆も作成できます：

```jldoctest gate_struct
julia> x_45_gate = x_45(1)
Gate Object: X45
Connected_qubits	: [1]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.9238795325112867 + 0.0im    0.0 - 0.3826834323650898im
0.0 - 0.3826834323650898im    0.9238795325112867 + 0.0im


julia> inv(x_45_gate)
Gate Object: Snowflurry.RotationX
Parameters: 
theta	: -0.7853981633974483

Connected_qubits	: [1]
Operator:
(2, 2)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
0.9238795325112867 + 0.0im    -0.0 + 0.3826834323650898im
-0.0 + 0.3826834323650898im    0.9238795325112867 + 0.0im


```

新しい`GateSymbol`型を含む`QuantumCircuit`の印刷を可能にするために、表示シンボルを次のように定義する必要があります：

```jldoctest gate_struct
julia> Snowflurry.gates_display_symbols[X45] = ["X45"];

```

この`Gate`がハードウェアQPUに命令として送信される場合、命令`String`を定義する必要があります：

```jldoctest gate_struct
julia> Snowflurry.instruction_symbols[X45] = "x45";

```

この`Gate`を含む回路を構築できます：

```jldoctest gate_struct
julia> circuit = QuantumCircuit(qubit_count = 2, instructions = [x_45_gate])
Quantum Circuit Object:
   qubit_count: 2
   bit_count: 2
q[1]:──X45──

q[2]:───────

```

さらに、次のようにして`Controlled{X45}`ゲートを構築できます：

```jldoctest gate_struct
julia> control = 1; target = 2;

julia> controlled(x_45(target), [control])
Gate Object: Controlled{X45}
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.9238795325112867 + 0.0im    0.0 - 0.3826834323650898im
0.0 + 0.0im    0.0 + 0.0im    0.0 - 0.3826834323650898im    0.9238795325112867 + 0.0im

```
