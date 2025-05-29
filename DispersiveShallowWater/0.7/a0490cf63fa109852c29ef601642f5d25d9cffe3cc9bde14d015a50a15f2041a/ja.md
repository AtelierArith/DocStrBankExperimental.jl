```
hamiltonian(q_global, equations, cache)
```

`q_global`の原始変数に対するハミルトニアンを`equations`のために返します。ハミルトニアンは保存量であり、解の導関数を含む場合があります。

`q_global`はすべてのノードにおける原始変数のベクトルです。`cache`は、非静水項が存在する場合に`solver`によって使用されるSBP演算子を保持する必要があります。

内部的に、この関数は出力用のベクトルを割り当て、[`DispersiveShallowWater.hamiltonian!`](@ref)を呼び出します。

!!! note
    この関数はすべての方程式に対して必ずしも実装されているわけではありません。サポートされている方程式の詳細については、[`DispersiveShallowWater.hamiltonian!`](@ref)を参照してください。

