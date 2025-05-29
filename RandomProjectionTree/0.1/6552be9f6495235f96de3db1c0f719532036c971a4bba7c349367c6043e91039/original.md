# function analyzeSplittingInfo(rptree::RPTree)

This function is used a posteriori to get statistics on how nodes were split.     Presently it computes statistics on leaves diameter.     It returns :

  * leaves = Array{TreeNode{KeyVector,RPTreeEvent}}()
  * leafDiameters : a Array{Float64,1} containing for each leaf its final diameter.
