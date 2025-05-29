tree_polish!(newt, models; tol = 10^-4, verbose = 1, topology = true)

Takes a tree and a model function, and optimizes branch lengths and, optionally, topology. Returns final LL. Set `verbose=0` to suppress output. Note: This is not intended for an exhaustive tree search (which requires different heuristics), but rather to polish a tree that is already relatively close to the optimum.
