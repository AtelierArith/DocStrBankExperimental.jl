bulkscan_null(Y, G, K, nb; reml = true)

Calculates the LOD scores for all pairs of traits and markers, by a (multi-threaded) loop over blocks of traits and the LiteQTL-type of approach

# Arguments

  * Y = 2d Array of Float; matrix of one trait or multiple traits
  * G = 2d Array of Float; matrix of genotype probabilities
  * K = 2d Array of Float; kinship matrix
  * nb = Int; number of blocks of traits required; ideally to be the same number of threads used for parallelization

# Value

  * LOD = 2d Array of Float; LOD scores for all pairs of traits and markers

# Notes:
