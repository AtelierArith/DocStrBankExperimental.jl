```julia
Domain(
    mesh_file::String,
    sections_in
) -> Cthonios.Domain{C, D, S, DBCs, Vector{Int64}, NBCs, NS, CPs} where {C<:(FiniteElementContainers.VectorizedNodalField{T, 2, _A, _B, _C} where {T<:Number, _A, _B, _C<:AbstractVector{T}}), D<:(FiniteElementContainers.DofManager{Int64, _A, _B, Vector{Float64}, _C} where {_A, _B, _C<:(AbstractArray{Int64})}), S<:NamedTuple, DBCs<:NamedTuple, NBCs<:NamedTuple, NS<:NamedTuple, CPs<:NamedTuple}
Domain(
    mesh_file::String,
    sections_in,
    dbcs_in
) -> Cthonios.Domain{C, D, S, DBCs, Vector{Int64}, NBCs, NS, CPs} where {C<:(FiniteElementContainers.VectorizedNodalField{T, 2, _A, _B, _C} where {T<:Number, _A, _B, _C<:AbstractVector{T}}), D<:(FiniteElementContainers.DofManager{Int64, _A, _B, Vector{Float64}, _C} where {_A, _B, _C<:(AbstractArray{Int64})}), S<:NamedTuple, DBCs<:NamedTuple, NBCs<:NamedTuple, NS<:NamedTuple, CPs<:NamedTuple}
Domain(
    mesh_file::String,
    sections_in,
    dbcs_in,
    nbcs_in
) -> Cthonios.Domain{C, D, S, DBCs, Vector{Int64}, NBCs, NS, CPs} where {C<:(FiniteElementContainers.VectorizedNodalField{T, 2, _A, _B, _C} where {T<:Number, _A, _B, _C<:AbstractVector{T}}), D<:(FiniteElementContainers.DofManager{Int64, _A, _B, Vector{Float64}, _C} where {_A, _B, _C<:(AbstractArray{Int64})}), S<:NamedTuple, DBCs<:NamedTuple, NBCs<:NamedTuple, NS<:NamedTuple, CPs<:NamedTuple}
Domain(
    mesh_file::String,
    sections_in,
    dbcs_in,
    nbcs_in,
    contact_pairs_in
) -> Cthonios.Domain{C, D, S, DBCs, Vector{Int64}, NBCs, NS, CPs} where {C<:(FiniteElementContainers.VectorizedNodalField{T, 2, _A, _B, _C} where {T<:Number, _A, _B, _C<:AbstractVector{T}}), D<:(FiniteElementContainers.DofManager{Int64, _A, _B, Vector{Float64}, _C} where {_A, _B, _C<:(AbstractArray{Int64})}), S<:NamedTuple, DBCs<:NamedTuple, NBCs<:NamedTuple, NS<:NamedTuple, CPs<:NamedTuple}

```

`Domain`型のコンストラクタ。`mesh_file` - 読み込むメッシュのファイル名。`sections_in` - `Section`のセット。`dbcs_in` - `DirichletBC`のセット。`nbcs_in` - `NeumannBC`のセット。
