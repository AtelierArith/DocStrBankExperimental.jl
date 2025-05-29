```
get_pauli(
    circuit::QuantumCircuit;
    imaginary_exponent::Integer=0,
    negative_exponent::Integer=0
)::PauliGroupElement
```

与えられた `circuit` に含まれるパウリゲートに基づいて `PauliGroupElement` を返します。

パウリ群の要素は $i^\delta (-1)^\epsilon \sigma_a$ に対応し、ここで $\delta$ と $\epsilon$ はそれぞれ `imaginary_exponent` と `negative_exponent` を指定することで設定されます。指数は 0 または 1 でなければなりません。デフォルト値は 0 です。$\sigma_a$ はパウリ演算子のテンソル積です。パウリ演算子は `circuit` で指定されます。

# 例

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 2);

julia> push!(circuit, sigma_x(1), sigma_y(2))
Quantum Circuit Object:
   qubit_count: 2 
   bit_count: 2 
q[1]:──X───────
               
q[2]:───────Y──
               



julia> get_pauli(circuit, imaginary_exponent=1, negative_exponent=1)
Pauli Group Element:
-1.0im*X(1)*Y(2)



```

`circuit` 内で同じ量子ビットに複数のパウリゲートが適用される場合、ゲートは最初のゲートが乗算の右端のゲートとなるように乗算されます。

```jldoctest
julia> circuit = QuantumCircuit(qubit_count = 1);

julia> push!(circuit, sigma_x(1), sigma_z(1))
Quantum Circuit Object:
   qubit_count: 1 
   bit_count: 1 
q[1]:──X────Z──
               



julia> get_pauli(circuit)
Pauli Group Element:
1.0im*Y(1)



```
