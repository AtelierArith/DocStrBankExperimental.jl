```
trajgwas(nullmeanformula, reformula, nullwsvarformula, idvar, covfile, geneticfile; kwargs...)
trajgwas(nullmeanformula, reformula, nullwsvarformula, idvar, df, geneticfile; kwargs...)
trajgwas(fittednullmodel, geneticfile; kwargs...)
trajgwas(fittednullmodel, bedfile, bimfile, bedn; kwargs...)
trajgwas(fittednullmodel, vcffile, nsamples, vcftype; kwargs...)
trajgwas(fittednullmodel, bgenfile, nsamples; kwargs...)
```

# Positional arguments

  * `nullmeanformula::FormulaTerm`: mean formula (β) for the null model.
  * `reformula::FormulaTerm`: random effects formula (γ) for the model.
  * `nullwsvarformula::FormulaTerm`: within-subject variance formula (τ) for the null model.
  * `idvar::Union{String, Symbol}`: id variable for groupings.
  * `covfile::AbstractString`: covariate file (csv) with one header line. One column   should be the longitudinal phenotype.
  * `df::DataFrame`: DataFrame containing response and regressors for null model.
  * `geneticfile::Union{Nothing, AbstractString}`: File containing genetic information for GWAS.   This includes a PLINK file name without the .bed, .fam, or .bim   extensions or a VCF file without the .vcf extension. If `geneticfile==nothing`,   only null model is fitted. If `geneticfile` is provided, bed, bim, and fam file (or vcf) with   the same `geneticfile` prefix need to exist. Compressed file formats such as gz and bz2   are allowed. Check all allowed formats by `SnpArrays.ALLOWED_FORMAT`. If you're using a VCF file,   make sure to use the `geneticformat = "VCF"` keyword option, and specificy dosage (:DS) or   genotype (:GT) data with the `vcftype` command.
  * `fittednullmodel::StatsModels.TableRegressionModel`: the fitted null model   output from `trajgwas(nullformula, covfile)` or `trajgwas(nullformula, df)`.   **NOTE** If the nullmodel is passed in with the `bedfile, bimfile, bedn` or    `vcffile, nsamples, vcftype` arguments, the IDs/data in the null model must match the   order of the IDs in the PLINK/VCF file.
  * `bedfile::Union{AbstractString,IOStream}`: path to Plink bed file with full file name.
  * `bimfile::Union{AbstractString,IOStream}`: path to Plink bim file with full file name.
  * `bedn::Integer`: number of samples in bed/vcf file.

# Keyword arguments

  * `analysistype`::AbstractString: Type of analysis to conduct. Default is `singlesnp`. Other options are `snpset` and `gxe`.
  * `geneticformat`::AbstractString: Type of file used for the genetic analysis. `"PLINK"` and `"VCF"` are currently supported. Default is PLINK.
  * `vcftype`::Union{Symbol, Nothing}: Data to extract from the VCF file for the GWAS analysis. `:DS` for dosage or `:GT` for genotypes. Default is nothing.
  * `nullfile::Union{AbstractString, IOStream}`: output file for the fitted null model;   default is `trajgwas.null.txt`.
  * `pvalfile::Union{AbstractString, IOStream}`: output file for the gwas p-values; default is   `trajgwas.pval.txt`.
  * `covtype::Vector{DataType}`: type information for `covfile`. This is useful   when `CSV.read(covarfile)` has parsing errors.
  * `covrowinds::Union{Nothing,AbstractVector{<:Integer}}`: sample indices for covariate file.
  * `testformula::FormulaTerm`: formula for test unit. Default is `@formula(trait ~ 0 + snp)`.
  * `test::Symbol`: `:score` (default) or `:wald`.
  * `disable_wsvar::Bool`: Disables test for within-sample variability for the Wald test. Default false.
  * `link::GLM.Link`: `LogitLink()` (default), `ProbitLink()`, `CauchitLink()`,   or `CloglogLink()`.
  * `snpmodel`: `ADDITIVE_MODEL` (default), `DOMINANT_MODEL`, or `RECESSIVE_MODEL`.
  * `snpinds::Union{Nothing,AbstractVector{<:Integer}}`: SNP indices for bed/vcf file.
  * `geneticrowinds::Union{Nothing,AbstractVector{<:Integer}}`: sample indices for bed/vcf file.
  * `samplepath::Union{Nothing, AbstractString}`: path for BGEN sample file if it's not encoded in the BGEN file.
  * `solver`: an optimizer supported by MathOptInterface. Default is   `Ipopt.Optimizer()`.
  * `solver_config`: Dict of configuration keys and values for the optimizer. Default is   `Dict("print_level" => 0, "mehrotra_algorithm" => "yes", "warm_start_init_point" => "yes",   "max_iter" => 100)`.
  * `runs::Integer`: Number of weighted NLS runs for the null model; default is 2.   Each run will use the newest `m.τ` and `m.Lγ` to update the weight matrices   `Vi` and solve the new weighted NLS.
  * `parallel::Bool`: Multi-threading or not for fitting the null model. Default is `false`.
  * `verbose::Bool`: default is `false`.
  * `snpset::Union{Nothing, Integer, AbstractString, AbstractVector{<:Integer}}`: Only include   if you are conducting a snpset analysis. An integer indicates a window of SNPs   (i.e. every 500 snps). An abstract string allows you to specify an input file,   with no header and two columns separated by a space. The first column must contain the snpset ID   and the second column must contain the snpid's identical to the bimfile. An AbstractVector   allows you to specify the snps you want to perform one joint snpset test for.
  * `e::Union{AbstractString,Symbol}`: Only include if you are conducting a GxE analysis.   Enviromental variable to be used to test the GxE interaction.   For instance, for testing `sex & snp` interaction, use `:sex` or `"sex"`.

# Examples

The following is an example of basic GWAS with PLINK files:

```julia
plinkfile = "plinkexample"
covfile = "covexample"
trajgwas(@formula(trait ~ sex), covfile, plkfile)
```

The following is an example of basic GWAS with a VCF file using dosages then genotypes:

```julia
vcffile = "vcfexample"
covfile = "covexample"
trajgwas(@formula(trait ~ sex), covfile, vcffile;
    geneticfile = "VCF", vcftype = :DS)

trajgwas(@formula(trait ~ sex), covfile, vcffile;
    geneticfile = "VCF", vcftype = :GT)
```

The following is an example of snpset GWAS (every 50 snps). For more types of snpset analyses see documentation:

```julia
trajgwas(@formula(trait ~ sex), covfile, plkfile;
    analysistype = "snpset", snpset = 50)
```

The following is an example of GxE GWAS testing the interaction effect:

```julia
trajgwas(@formula(trait ~ sex), covfile, plkfile;
    analysistype = "gxe", e = :sex)
```
