```
struct Boundary{S<:Symbol, UR<:UnitRange{<:Integer}}
    name::S         # Boundary patch name
    IDs_range::UR   # range to access boundary info (faces and boundary_cellsID)
end
```
