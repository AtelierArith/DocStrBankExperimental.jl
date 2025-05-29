# function analyzeSplittingInfo(rptree::RPTree)

この関数は、ノードがどのように分割されたかの統計を得るために事後的に使用されます。 現在、葉の直径に関する統計を計算します。 返されるものは：

  * leaves = Array{TreeNode{KeyVector,RPTreeEvent}}()
  * leafDiameters : 各葉の最終的な直径を含む Array{Float64,1}。
