unset!(commp::CommunityProfile, sample::AbstractString, prop::Symbol)

Delete a metadata entry in `sample` from CommunityProfile `commp` using the Symbol `prop`.  If you want an error to be thrown if the value does not exist, use [`delete!`](@ref).
