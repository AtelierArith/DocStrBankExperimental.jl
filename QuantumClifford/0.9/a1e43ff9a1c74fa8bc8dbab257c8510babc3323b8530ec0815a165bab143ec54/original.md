A tableau representation for mixed stabilizer states that keeps track of the destabilizers in order to provide efficient projection operations.

The rank `r` of the `n`-qubit tableau is tracked, either so that it can be used to represent a mixed stabilizer state, or so that it can be used to represent an `n-r` logical-qubit code over `n` physical qubits. The "logical" operators are tracked as well.

When the constructor is called on an incomplete [`Stabilizer`](@ref) it automatically calculates the destabilizers and logical operators, following chapter 4 of [gottesman1997stabilizer](@cite). Under the hood the conversion uses the [`canonicalize_gott!`](@ref) canonicalization. That canonicalization permutes the columns of the tableau, but we automatically undo the column permutation in the preparation of a `MixedDestabilizer` so that qubits are not reindexed. The boolean keyword arguments `undoperm` and `reportperm` can be used to control this behavior and to report the permutations explicitly.

See also: [`stabilizerview`](@ref), [`destabilizerview`](@ref), [`logicalxview`](@ref), [`logicalzview`](@ref)
