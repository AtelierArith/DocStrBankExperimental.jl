量子レジスタ全体に対するスタビライザ測定。

`projectrand!(state, pauli)` と `apply!(state, PauliMeasurement(pauli))` は同じ（おそらく非決定論的な）結果を与えます。特に [`Register`](@ref) に作用する際に便利です。

他にも: [`apply!`](@ref), [`projectrand!`](@ref)。
