# RPTreeArg

collects the argument for tree growing

FIELDS

  * D : the metric to use to compute all distances
  * depth : The maximum depth of the tree
  * threshold : the ratio between the mean (meanD) and the max (maxD) of distances between 2 objetcs in node.

    and the  maxDiameter and mean distance between 2 objects above which  we split by diameter.   If maxD / meanD > threshold we split by diameter to reach some sphericity in the node   else we split by projection.  So with threshold = 1. we always use split by diameter rule and the higher   threshold the more split nodes by the Projection rule.

    The function analyzeSplittingInfo can be used to get information on the splitting after a run  and adjust threshold depending on the information obtained.

CONSTRUCTORS

RPTreeArg(D::Distances.SemiMetric, depth::Int64, thresh::Float64)
