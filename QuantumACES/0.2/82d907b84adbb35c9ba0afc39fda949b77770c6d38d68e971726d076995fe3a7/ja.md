```
parse_qiskit_dict(counts::Dict{String, Int}, shots::Integer, qiskit_qubit_num::Integer; qiskit_qubit_map::Union{Vector{Int}, Nothing} = nothing)
```

Qiskitによって出力された辞書`counts`から決定された`UInt8`回路結果の解析されたStim互換行列を返します。`shots`ショットで、回路は`qiskit_qubit_num`量子ビットに作用し、`qiskit_qubit_map`が`nothing`でない場合、マップに含まれていない量子ビットの測定結果が0であることを確認します。
