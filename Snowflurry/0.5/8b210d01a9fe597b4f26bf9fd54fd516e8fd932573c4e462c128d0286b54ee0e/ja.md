```
get_measurement_probabilities(
    circuit::QuantumCircuit,
    [target_qubits::Vector{<:Integer}]
)::AbstractVector{<:Real}
```

`circuit`内の`target_qubits`の測定確率のリストを返します。

`target_qubits`が提供されていない場合、すべての量子ビットに対して確率が計算されます。

測定確率は、計算基底状態の最小から最大までの順にリストされます。たとえば、2量子ビットの[`QuantumCircuit`](@ref)の場合、確率は$\left|00\right\rangle$、$\left|01\right\rangle$、$\left|10\right\rangle$、および$\left|11\right\rangle$の順にリストされます。

!!! note
    伝統的に、量子ビット1は最も左のビットであり、その後に続くすべての量子ビットがあります。記法$\left|10\right\rangle$は、量子ビット1が状態$\left|1\right\rangle$にあり、量子ビット2が状態$\left|0\right\rangle$にあることを示します。


# 例

次の例では、$\left|10\right\rangle$を測定する確率が50%、$\left|11\right\rangle$を測定する確率も50%である`QuantumCircuit`を構築します：

```jldoctest get_circuit_measurement_probabilities
julia> circuit = QuantumCircuit(qubit_count = 2);

julia> push!(circuit, hadamard(1), sigma_x(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H───────
               
q[2]:───────X──
               



julia> get_measurement_probabilities(circuit)
4-element Vector{Float64}:
 0.0
 0.4999999999999999
 0.0
 0.4999999999999999

```

同じ`circuit`に対して、量子ビット2を測定して1を見つける確率は100%です：

```jldoctest get_circuit_measurement_probabilities
julia> target_qubit = [2];

julia> get_measurement_probabilities(circuit, target_qubit)
2-element Vector{Float64}:
 0.0
 0.9999999999999998

```
