A type representing the parameters used in a typical FACS screen.

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

  * `σ`: The standard deviation expected for cells during FACS sorting. This should be set according to the biological variance experimentally observed, e.g. in the fluorescence intensity of isogenic cells
  * `bin_info`: Range of guide phenotypes to collect in each bin

    # Example

    In the following example

    ```julia
    p = 0.05
    bin_info = Dict(:bin1 => (0.0, p), :bin2 => (1.0-p, 1.0))
    ```

    The 5th percentile of cells sorted according to their phenotype (fluorescence, size, etc) will be compared to the 95th percentile.

  * `bottleneck_representation`: Number of cells sorted expressed as an integer multiple of the number of guides
  * `seq_depth`: Sequencing depth as a integer multiple of the number of guides, i.e. `seq_depth=10` is equivalent to `10 * num_genes * coverage` reads.
