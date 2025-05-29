```
get_pauli(
    gate::AbstractGateSymbol,
    num_qubits::Integer;
    imaginary_exponent::Integer=0,
    negative_exponent::Integer=0
)::PauliGroupElement
```

`gate`と量子ビットの数に基づいて`PauliGroupElement`を返します。

パウリ群の要素は、$i^\delta (-1)^\epsilon \sigma_a$に対応し、ここで$\delta$と$\epsilon$はそれぞれ`imaginary_exponent`と`negative_exponent`を指定することで設定されます。指数は0または1でなければなりません。デフォルト値は0です。$\sigma_a$については、パウリ演算子のテンソル積です。この`get_pauli`関数のバリアントでは、`gate`を提供することで単一のパウリ演算子が設定されます。量子ビットの数は`num_qubits`で指定されます。

# 例

```jldoctest
julia> gate = sigma_x(2);

julia> num_qubits = 3;

julia> get_pauli(gate, num_qubits)
Pauli Group Element:
1.0*X(2)



```
