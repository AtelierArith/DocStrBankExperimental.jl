addLasserreBlock!(m::FlagModel{T,N,D}) where {T<:Flag,N,D}

Adds an empty Lasserre block of internal flag type 'T' to 'm' and returns it. One should then use 'addFlag' to add generators to the block. 
