```
WindowMPS{A<:GenericMPSTensor,B<:MPSBondTensor} <: AbstractFiniteMPS
```

Type that represents a finite Matrix Product State embedded in an infinte Matrix Product State.

## Fields

  * `left_gs::InfiniteMPS` – left infinite environment
  * `window::FiniteMPS` – finite window Matrix Product State
  * `right_gs::InfiniteMPS` – right infinite environment

---

## Constructors

```
WindowMPS(left_gs::InfiniteMPS, window_state::FiniteMPS, [right_gs::InfiniteMPS])
WindowMPS(left_gs::InfiniteMPS, window_tensors::AbstractVector, [right_gs::InfiniteMPS])
WindowMPS([f, eltype], physicalspaces::Vector{<:Union{S, CompositeSpace{S}},
          virtualspaces::Vector{<:Union{S, CompositeSpace{S}}, left_gs::InfiniteMPS,
          [right_gs::InfiniteMPS])
WindowMPS([f, eltype], physicalspaces::Vector{<:Union{S,CompositeSpace{S}}},
          maxvirtualspace::S, left_gs::InfiniteMPS, [right_gs::InfiniteMPS])
```

Construct a WindowMPS via a specification of left and right infinite environment, and either a window state or a vector of tensors to construct the window. Alternatively, it is possible to supply the same arguments as for the constructor of [`FiniteMPS`](@ref), followed by a left (and right) environment to construct the WindowMPS in one step.

!!! note
    By default, the right environment is chosen to be equal to the left, however no copy is made. In this case, changing the left state will also affect the right state.

    WindowMPS(state::InfiniteMPS, L::Int)


Construct a WindowMPS from an InfiniteMPS, by promoting a region of length `L` to a `FiniteMPS`.
