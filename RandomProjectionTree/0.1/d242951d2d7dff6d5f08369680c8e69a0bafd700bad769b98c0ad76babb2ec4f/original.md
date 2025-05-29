# function randomProjection(rptree::RPTree)

The driver method that grow a tree up to argument depth. 

The splitting of nodes is parallelised:

  * if $nworkers() > 1$ the first node is split the left and right children are   are affected to two independents tasks via @spawnat : any.
  * Furthermore if $Threads.nthreads() > 1$ the next generation of children   is split in 2 independent threads, thus giving 4 independants sub trees generated   in parallel.

## Returns:

  * an Array{Vector{Float64},1} storing the center of leaves data vectors.

NOTA : The method cannot be run twice on the same rptree. A new RPTree must be initialized.
