A type representing the parameters used in a typical growth-based screen.

  * `num_genes`: Number of genes targeted by the screen
  * `coverage`: Number of guides per gene
  * `representation`: Number of cells with each guide. `representation=10` means that there are 10 times as many cells as guides during transfection. The actual number of cells per guide post-transfection will be less depending on the MOI
  * `moi`: The multiplicity of infection, $\lambda$, of the screen. We model this as a Poisson process during transfection (see [`Crispulator.transfect`](@ref)).

    !!! note
        We **do not** model multiple infections. We assume that the MOI is properly selected and less than half the cells are transfected by any virus, i.e. $\lambda \lt 0.5$ and then select only the cells that have a single transfection occurrence:

        $$
        P(x = 1; Poisson(λ))
        $$

        For $\lambda = 0.25$ this works out to being $\approx 19.5\%$ of the number of cells (`num_genes` * `coverage` * `representation`).

  * `seq_depth`: Sequencing depth as a integer multiple of the number of guides, i.e. `seq_depth=10` is equivalent to `10 * num_genes * coverage` reads.

  * `bottleneck_representation`: For growth screens, how much of a bottleneck is applied. This is minimum number of cells that is kept when passaging the pool of cells. This is expressed as an integer multiple of the number of guides.
  * `num_bottlenecks`: For growth screens, how many bottlenecks are applied. This is the integer number of passages during the growth screen.
  * `noise`: Before each passage, the theoretical phenotype of each cell is convolved with a normal noise distribution with a standard deviation, σ, dictated by this parameter. This should be set based on an expectation of noisiness of the subsampling
