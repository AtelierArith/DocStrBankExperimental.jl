optimalbandwidth(k::HAC{T}, mm; prewhite::Bool=false) where {T<:Andrews} optimalbandwidth(k::HAC{T}, mm; prewhite::Bool=false) where {T<:NeweyWest}

Calculate the optimal bandwidth according to either Andrews or Newey-West.
