```
CellState(
names::AbstractVector{S},
volumes::AbstractVector{T},
counts::AbstractVector{T};
options...) where {S<:Symbol, T<:Integer}


CellState(;names::AbstractVector{Symbol}, volumes::AbstractVector{T}, counts::AbstractVector{T}, options...) where T<:Integer
```

Create a new `CellState` where each row corresponds to a cell.

By default, this function generates a table with the following columns:

  * names`::Vector{Symbol}` – List of names given to cells (e.g. `:TCell`)
  * cellIDs`::Vector{<:Integer}` – A unqiue number given to a cell
  * typeIDs`::Vector{<:Integer}` – A number corresponding to the cell's name
  * volumes`::Vector{<:Integer}` – Number of grid squares occupied
  * desiredVolumes`::Vector{<:Integer}`– Desired number of grid squares
  * perimeters`::Vector{<:Integer}`– Cell border penality
  * desiredPerimeters`::Vector{<:Integer}`– Desired cell border penality

The first row in the table is reserved for `:Medium` which is the name given to grid locations not belonging to any cell and is given an index of 0 (The first cell is given an index of 1).

Additional cell properties can be supplied as keyword arguements. The length of the keyword arguement needs to match the number of cell types or the total cell count.      
