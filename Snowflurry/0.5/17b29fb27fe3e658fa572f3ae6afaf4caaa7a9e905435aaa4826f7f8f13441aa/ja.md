```
simulate(circuit::QuantumCircuit)::Ket
```

`circuit`の理想的なシミュレーションを実行し、最終的な量子状態（すなわち波動関数）を返します。シミュレーターは、初期状態$\Psi$がゼロ番目のフォック基底に対応すると仮定します。すなわち、`ψ = fock(0, 2^get_num_qubits(circuit))`です。ゼロ番目のフォック基底は、ほとんどの超伝導量子プロセッサの初期状態に対応します。すなわち：

$$
|\Psi\rangle = |0\rangle^{\otimes n},
$$

ここで、$n$は量子ビットの数です。

!!! note
    入力`circuit`には`Readout`命令を含めてはいけません。`Readout`命令を含む`circuits`のシミュレーションには[`simulate_shots`](@ref)を使用してください。


シミュレーションは、[Suzuki *et. al.* (2021)](https://doi.org/10.22331/q-2021-10-06-559)のリスト5で説明されているアプローチを利用しています。

# 例

```jldoctest
julia> c = QuantumCircuit(qubit_count = 2);

julia> push!(c, hadamard(1))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H──
          
q[2]:─────
          


julia> push!(c, control_x(1, 2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──H────*──
            |  
q[2]:───────X──
               


julia> ket = simulate(c)
4-element Ket{ComplexF64}:
0.7071067811865475 + 0.0im
0.0 + 0.0im
0.0 + 0.0im
0.7071067811865475 + 0.0im


```
