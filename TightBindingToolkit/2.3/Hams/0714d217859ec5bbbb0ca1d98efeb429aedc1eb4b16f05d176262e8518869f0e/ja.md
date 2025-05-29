```julia
ModifyHamiltonianField!(Ham::Hamiltonian, uc::UnitCell, newFields::Vector{Float64} ; dim::Int64=4, verbose::Bool=false)
```

ハミルトニアンのオンサイトフィールド部分のみを変更するための高速な実装です。`newFields`は`uc.basis`と同じ長さのベクトルでなければなりません。`dim`はオプションの引数で、どのオンサイトフィールドの要素が置き換えられるかを決定します。
