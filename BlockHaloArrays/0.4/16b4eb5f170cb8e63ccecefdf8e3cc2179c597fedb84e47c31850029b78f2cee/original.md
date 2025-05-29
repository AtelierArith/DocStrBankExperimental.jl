Determine if the block is on the boundary

# Arguments

  * `A::AbstractBlockHaloArray`: The array in question
  * `blockid::Integer`: The id of the block. This is normally associated with the thread id
  * `boundary::Symbol`: Which boundary are we checking for? Examples include :ilo, :jhi, etc...
