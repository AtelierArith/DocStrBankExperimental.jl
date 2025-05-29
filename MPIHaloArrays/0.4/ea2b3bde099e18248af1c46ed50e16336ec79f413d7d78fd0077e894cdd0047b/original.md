Helper functions to get the low side halo and domain starting/ending indices

# Arguments

  * `field`: Array
  * `dim`: Dimension to check indices on
  * `nhalo`: Number of halo entries

# Return

  * `NTuple{Int, 4}`: The set of lo indices (lo*halo*start, lo*halo*end, lo*domain*start, lo*domain*end).
