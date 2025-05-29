Calculate the second Chern numbers in the four-dimensional case with reference to Fukui-Hatsugai-Suzuki method [Fukui2005Chern,Mochol-Grzelak2018Efficient](@cite).

```
calcSecondChern(Hamiltonian::Function; Nfill::T1=nothing, N::T2=(30, 30, 30, 30), returnRealValue::Bool=true, parallel::T3=UseSingleThread()) where {T1<:Union{Int,Nothing},T2<:Union{AbstractVector,Tuple},T3<:TopologicalNumbersParallel}
```

Arguments

  * `Hamiltionian`: The Hamiltonian matrix with two-dimensional wavenumber `k` as an argument.
  * `Nfill::T1`: The filling number. The default value is `Hs ÷ 2`, where `Hs` is the size of the Hamiltonian matrix.
  * `N::T2`: The numbers of meshes when discretizing the Brillouin Zone. Each element of `N` is the number of meshes in the x, y, z, and w directions, respectively.
  * `returnRealValue::Bool`: An option to return the value of the topological number by an real value. The topological number returns a value of type `Float64` when `true`, and a value of type `ComplexF64` when `false`.

# Examples
