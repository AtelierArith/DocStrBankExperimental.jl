bulkscan*alt*grid(Y, G, K, hsq_list)

Calculates LOD scores for all pairs of traits and markers for each heritability in the supplied list, and returns the      maximal LOD scores for each pair among all calculated ones

# Arguments

  * Y = 2d Array of Float; traits
  * G = 2d Array of Float; genotype probabilities
  * K = 2d Array of Float; kinship matrix
  * hsq_list = 1d array of Float; the list of heritabilities requested to choose from

# Value

  * maxL = 2d Array of Float; matrix of LOD scores for all traits and markers estimated

# Notes:

Maximal LOD scores are taken independently for each pair of trait and marker; while the number of candidated hsq's are finite,     doing such maximization is like performing maximum-likelihood approach on discrete values for the heritability parameter;     this is a shortcut of doing the exact scan_alt() independently for each trait and each marker.
