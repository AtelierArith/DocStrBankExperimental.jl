```
permute_qubits!(
    circuit::QuantumCircuit,
    qubit_mapping::AbstractDict{T,T}
) where T<:Integer
```

`circuit`を修正して、`qubit_mapping`に基づいてゲートを他の量子ビットに移動します。

辞書`qubit_mapping`は、ターゲット量子ビットを更新する方法を説明するキーと値のペアを含んでいます。キーは変更するターゲット量子ビットを示し、関連する値は新しい量子ビットを指定します。辞書内のすべてのキーは値として存在し、逆もまた同様でなければなりません。

例えば、`Dict(1 => 2)`は有効な`qubit_mapping`ではありませんが、`Dict(1 => 2, 2 => 1)`は有効です。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 3);

julia> push!(c, sigma_x(1), hadamard(2), sigma_y(3))
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:──X────────────
                    
q[2]:───────H───────
                    
q[3]:────────────Y──                    



julia> permute_qubits!(c, Dict(1 => 3, 3 => 1))

julia> show(c)
Quantum Circuit Object:
   qubit_count: 3 
   bit_count: 3 
q[1]:────────────Y──
                    
q[2]:───────H───────
                    
q[3]:──X────────────
                    


```
