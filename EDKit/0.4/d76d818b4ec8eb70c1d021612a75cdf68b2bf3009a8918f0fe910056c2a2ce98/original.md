covmat(ol::AbstractVector, v::AbstractVecOrMat{<:Number})

Return the covariant matrix for a given list of operators:     Cᵢⱼ = 1/2⟨v|{hᵢ,hⱼ}|v⟩ - ⟨v|hᵢ|v⟩⟨v|hⱼ|v⟩, or for a set of vector,     Cᵢⱼ = 1/2Tr[ρ{hᵢ,hⱼ}] - Tr[ρhᵢ]Tr[ρhⱼ], where ρ = 1/N∑ₙ|vₙ⟩⟨vₙ|.

## Inputs:

  * `ol`: List of operators, represented by matrices or `Operator`s.
  * `V` : Target state represented by a vector, or target states represented by a matrix.

## Outputs:

  * cm: (Symmetric real) matrix.
