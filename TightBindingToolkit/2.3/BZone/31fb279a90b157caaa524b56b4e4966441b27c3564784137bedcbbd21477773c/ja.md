```julia
GetBZPath(bz::BZ, start::Vector{Float64}, ending::Vector{Float64} ; nearest::Bool = false, exclusive::Bool = true) --> Vector{Vector{Float64}}
```

`BZ`の離散化された実際のパスを返します。このパスは、2つのモーメンタム`start`と`ending`を結びます。オプションの入力`nearest`は[`GetQIndex`](@ref)と同じで、`exclusive`は[`GetIndexPath`](@ref)と同じです。
