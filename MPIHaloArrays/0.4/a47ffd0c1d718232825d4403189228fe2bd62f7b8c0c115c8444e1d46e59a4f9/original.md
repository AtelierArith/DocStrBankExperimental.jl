Helper functions to get the high side halo and domain starting/ending indices

# Arguments

  * `field`: Array
  * `dim`: Dimension to check indices on
  * `nhalo`: Number of halo entries

# Return

  * `NTuple{Int, 4}`: The set of lo indices (hi*domain*start, hi*domain*end, hi*halo*start, hi*halo*end.
