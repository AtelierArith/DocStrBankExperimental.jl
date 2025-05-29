Psplits(w::AbstractVector, P::Integer, strategy::String)

Given weight vector `w` depending on partioning strategy splits indexes of elements of `w` to P sets. If some of the sets are empty, they are dropped.  So, make sure that the number of partitions provided is a meaningful number. 

The partions are formed according to the strategy. Possible strategies include "equalsize", "equalrange", "snake" and "random".

Returns P sets of partioned indexes.
