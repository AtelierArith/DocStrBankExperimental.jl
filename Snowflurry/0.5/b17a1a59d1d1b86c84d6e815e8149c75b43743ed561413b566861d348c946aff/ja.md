```
Controlled{G<:AbstractGateSymbol}<:AbstractGateSymbol
```

`Controlled`オブジェクトは、`Operator`（`kernel`）と対応する制御キュービットの数を使用して、制御された`AbstractGateSymbol`を構築することを可能にします。ヘルパー関数`controlled`を使用すると、制御された`AbstractGateSymbol`と制御された`Gate`の両方を簡単に作成できます。`apply_gate`への呼び出しは、最適化されたルーチンが存在する場合はそれにディスパッチされます。そうでない場合は、オペレーターを同等の`DenseOperator`にキャストし、作成されたオペレーターを適用することになります。

# 例

`controlled`関数を使用して、制御されたハダマールゲートを作成できます：

```jldoctest controlled_hadamard
julia> controlled_hadamard = controlled(hadamard(2), [1])
Gate Object: Controlled{Snowflurry.Hadamard}
Connected_qubits	: [1, 2]
Operator:
(4, 4)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.7071067811865475 + 0.0im    0.7071067811865475 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.7071067811865475 + 0.0im    -0.7071067811865475 + 0.0im

```

その後、他の`Gate`と同様に`QuantumCircuit`で使用でき、その表示シンボルは単一ターゲットの`Hadamard` `Gate`の表示シンボルから継承されます：

```jldoctest controlled_hadamard
julia> circuit=QuantumCircuit(qubit_count=2,instructions = [controlled_hadamard])
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──*──
       |  
q[2]:──H──
          
```

一般に、任意の数のターゲットと制御を持つ`Controlled`構造体を構築できます。たとえば、次の例は、`control_qubits=[1,2]`および`target_qubit=[3]`を持つ`ConnectedGate{SigmaX}`として、`Toffoli` `Gate`の同等のものを構築します：

```jldoctest
julia> toffoli_as_controlled_gate = controlled(sigma_x(3), [1, 2])
Gate Object: Controlled{Snowflurry.SigmaX}
Connected_qubits	: [1, 2, 3]
Operator:
(8, 8)-element Snowflurry.DenseOperator:
Underlying data ComplexF64:
1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im
0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    0.0 + 0.0im    1.0 + 0.0im    0.0 + 0.0im
```
