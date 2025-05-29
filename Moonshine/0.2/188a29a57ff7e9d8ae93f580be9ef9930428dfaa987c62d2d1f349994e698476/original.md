impedance(arg[, ss, ds]; estack, edgesmap, vqueue, visited) impedance!(arg, ss, ds C, Z2; estack, edgesmap, vqueue, visited) impedance_matrix(arg, estack, edgesmap)

Compute impedances. A set of source and destination vertices can be provided through arguments `ss` and `ds` respectively. Otherwise, impedances are computed pairwise between leaves.
