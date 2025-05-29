```
find_representation(
    symvals::AbstractVector{<:Number}, 
    lgirs::AbstractVector{<:AbstractIrrep},
    assert_return_T::Type{<:Union{Integer, AbstractFloat}}=Int);
    αβγ::Union{AbstractVector{<:Real},Nothing}=nothing,
    atol::Real=DEFAULT_ATOL,
    maxresnorm::Real=1e-3,
    verbose::Bool=false
)                                          --> Union{Nothing, Vector{assert_return_T}}
```

From a vector (or vector of vectors) of symmetry eigenvalues `symvals` sampled along all the operations of a group gᵢ, whose irreps are contained in `irs` (evaluated with optional free  parameters `αβγ`), return the multiplicities of each irrep.

Optionally, the multiciplities' element type can be specified via the `assert_return_T` argument (performing checked conversion; returns `nothing` if representation in  `assert_return_T` is impossible). This can be useful if one suspects a particular band to  transform like a fraction of an irrep (i.e., the specified symmetry data is incomplete).

If no valid set of multiplicities exist (i.e., is solvable, and has real-valued and `assert_return_T` representible type), the sentinel value `nothing` is returned. Optional debugging information can in this case be shown by setting `verbose=true`.

# Extended help

Effectively, this applies the projection operator P⁽ʲ⁾ of each irrep's character set χ⁽ʲ⁾(gᵢ) (j = 1, ... , Nⁱʳʳ) to the symmetry data sᵢ ≡ `symvals`:

```
P⁽ʲ⁾  ≡ (dⱼ/|g|) ∑ᵢ χ⁽ʲ⁾(gᵢ)*gᵢ         [characters χ⁽ʲ⁾(gᵢ), irrep dimension dⱼ]
P⁽ʲ⁾s = (dⱼ/|g|) ∑ᵢ χ⁽ʲ⁾(gᵢ)*sᵢ = nⱼ,   [number of bands that transform like jth irrep]
```

returning the irrep multiplicities mⱼ ≡ nⱼ/dⱼ.
