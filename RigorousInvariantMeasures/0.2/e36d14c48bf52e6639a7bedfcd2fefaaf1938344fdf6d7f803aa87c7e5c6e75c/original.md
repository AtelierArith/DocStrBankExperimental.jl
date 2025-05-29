Dynamic based on a piecewise monotonic map.

The map is defined as T(x) = Ts[k](x) if $x \in [endpoints[k], endpoints[k+1])$.

`y_endpoints` ($k \times 2$ matrix) contains the result of applying Ts to the endpoints of each interval. These can be filled in automatically from `endpoints`, but sometimes they are known to higher accuracy, for instance for `x -> mod(3x, 1)` we know that it is full-branch exactly. It is assumed that the map will send its domain hull(endpoints[begin],endpoints[end]) into itself.

the array `branches` is guaranteed to satisfy branches[i].X[end]==branches[i+1].X[begin]
