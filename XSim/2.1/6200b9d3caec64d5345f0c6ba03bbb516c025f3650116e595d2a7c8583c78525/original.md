# Selection function

```
select(cohort      ::Cohort,
       n           ::Int64,
       criteria    ::Union{String, Array} = "phenotypes";
       h2          ::Union{Array{Float64}, Float64}=GLOBAL("h2"),
       ve          ::Union{Array{Float64}, Float64}=GLOBAL("Ve"),
       weights     ::Array{Float64, 1}  =[1.0],
       return_log  ::Bool               =false,
       is_random   ::Bool               =false,
       silent      ::Bool               =GLOBAL("silent")

select(cohort::Cohort, ratio::Float64; args...)
```

### Arguments

Positional arguments

  * `cohort` : A `cohort` from which individuals are selected.
  * `n` : `n` individuals are selected.
  * `ratio` : `ratio` portion of individuals are selected.
  * `criteria` : `Criteria` that will be used for the selecition. Default "phenotypes", the options are ["phenotypes", "GBLUP", array]. If set to "GBLUP",  a genetic evaluation is carried out by `JWAS` and the estimated breeding values will be the `criteria`. It's also avaialbe to provdie the `criteria` (e.g., phenotypes matrix) directly for the selection.

Keyword arguments

  * `h2` : The heritability `h2` of the simulated phenotypes.
  * `ve` : The residual covariance `ve` of the simulated phenotypes.
  * `weight` : Linear coefficients of traits for the selection. The selection is more sensitive to traits with greater `weight`. Negative
  * `return_log` : Default `false`. Set `true` to return selection differential and selection response besides the selected cohort.
  * `silent` : Default `false`. Set `true` to mute the log messages.

### Outputs

A selected `cohort` object will be returned. If `return_log` is set to `true`, a `dictionary` object containing the selected cohort, selection differential, and selection response will be returned.

─────────────────────────────────────────────────────────

### Example

#### Single Trait Selection

Set demo genome and phenome with single traits controlled by 50 QTLs.

```jldoctest
julia> build_demo()
julia> build_phenome(50)
julia> summary()
[ Info: --------- Genome Summary ---------
[ Info: Number of Chromosome  : 10
[ Info: 
[ Info: Chromosome Length (cM): 1500.0
[ Info: [150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0]
[ Info: 
[ Info: Number of Loci        : 1000
[ Info: [100, 100, 100, 100, 100, 100, 100, 100, 100, 100]
[ Info: 
[ Info: Genotyping Error      : 0.0
[ Info: Mutation Rate         : 0.0
[ Info: 
[ Info: --------- Phenome Summary ---------
[ Info: Number of Traits      : 1
[ Info: Heritability (h2)     : [0.5]
┌ Info: 
│   Genetic_Variance =
│    1×1 Array{Float64,2}:
└     1.0
┌ Info: 
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: Number of QTLs        : [50]
```

Initialize a cohort with 100 individuals

```jldoctest
julia> cohort = Cohort(100)
```

##### Select 30 individuals

```jldoctest
# Select top 30 individuals
julia> cohort_s = select(cohort, 30)
# Equivalent
julia> cohort_s = select(cohort, 0.3)

[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [1.174]
[ Info: Selection response     (G): [0.843]
┌ Info:
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info:
[ Info: Mean of breeding values:
[ Info: [1.448]
[ Info:
[ Info: Variance of breeding values:
[ Info: [0.367]
```

##### Assign Heritability `h2` or Residual Covariance `ve`

```jldoctest
# Assign heritability
julia> progenies = select(cohort, 30, h2=0.1)

# Equivalent in the case where genetic variance `vg` is 1.0
julia> progenies = select(cohort, 30, ve=9.0)

[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [1.182]
[ Info: Selection response     (G): [0.338]
┌ Info:
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     9.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [0.956]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.643]
```

##### Negative Selection

Set `is_positive=false` to rank individuals in ascending order

```jldoctest
julia> progenies = select(cohort, 30, is_positive=false)
[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [-1.19]
[ Info: Selection response     (G): [-0.89]
┌ Info: 
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [-0.24]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.566]
```

##### Random Selection

```jldoctest
julia> progenies = select(cohort, 30, is_random=true)
[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [-0.06]
[ Info: Selection response     (G): [-0.191]
┌ Info: 
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     1.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [0.441]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.946]
```

##### Selection wiht Multiple Parameters

It's possible specify multiple parameters described above in one selection. User can either enclose parameters as keyword arguments, or pass them through a `dictionary` object.

```jldoctest
# Keyword args
julia> progenies = select(cohort, 30, h2=0.3, is_positive=false)

# Equivalent
julia> args = Dict(:h2=>0.3,
                   :is_positive=>false)
julia> progenies = select(cohort, 30; args...)

[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [-1.086]
[ Info: Selection response     (G): [-0.486]
┌ Info: 
│   Residual_Variance =
│    1×1 Array{Float64,2}:
└     2.3333333333333335
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [0.154]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.818]
```

─────────────────────────────────────────────────────────

#### Multi-Trait Selection

Set demo genome and phenome with single traits controlled by 50 QTLs.

```jldoctest
julia> build_demo()
julia> summary()
[ Info: --------- Genome Summary ---------
[ Info: Number of Chromosome  : 10
[ Info: 
[ Info: Chromosome Length (cM): 1500.0
[ Info: [150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0, 150.0]
[ Info: 
[ Info: Number of Loci        : 1000
[ Info: [100, 100, 100, 100, 100, 100, 100, 100, 100, 100]
[ Info: 
[ Info: Genotyping Error      : 0.0
[ Info: Mutation Rate         : 0.0
[ Info: 
[ Info: --------- Phenome Summary ---------
[ Info: Number of Traits      : 2
[ Info: Heritability (h2)     : [0.5, 0.5]
┌ Info: 
│   Genetic_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
┌ Info: 
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.0
└     0.0  1.0
[ Info: Number of QTLs        : [3 8]
```

Initialize a cohort with 100 individuals

```jldoctest
julia> cohort = Cohort(100)
```

##### Assign Heritabilities for Multiple Traits

```jldoctest
julia> progenies = select(cohort, 30, h2=[0.9, 0.3])
[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [0.468 1.028]
[ Info: Selection response     (G): [0.383 0.636]
┌ Info: 
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     0.111111  0.0
└     0.0       2.33333
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [-0.889 0.28]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.947 0.625]
```

##### Assign Trait Correlations via Residual Covariance

```jldoctest
julia> progenies = select(cohort, 30, ve=[1   0.3
                                          0.3   1])
[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [0.866 0.925]
[ Info: Selection response     (G): [0.662 0.762]
┌ Info: 
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     1.0  0.3
└     0.3  1.0
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info: 
[ Info: Mean of breeding values: 
[ Info: [-0.608 0.406]
[ Info: 
[ Info: Variance of breeding values: 
[ Info: [0.549 0.476]
```

##### Derive Selection Index for Multiple Traits

Assigning a vector to the parameter `weights` to derive a selection index which is a linear combintation of the weights and the phenotypes.  In this example, we demonstrate two traits with the heritability of 0.3 and 0.8, respectively. And we can select traits with more weight on the second trait which is more heritable, and negatively select the first trait.

```jldoctest
julia> progenies = select(cohort, 30, h2=[.3, .8], weights=[-0.1, 0.9])
[ Info: --------- Selection Summary ---------
[ Info: Select 30 individuals out of 100 individuals
[ Info: Selection differential (P): [-0.318 1.027]
[ Info: Selection response     (G): [-0.233 0.869]
┌ Info:
│   Residual_Variance =
│    2×2 Array{Float64,2}:
│     2.33333  0.0
└     0.0      0.25
[ Info: --------- Offsprings Summary ---------
[ Info: Cohort (30 individuals)
[ Info:
[ Info: Mean of breeding values:
[ Info: [-1.508 0.513]
[ Info:
[ Info: Variance of breeding values:
[ Info: [1.053 0.458]
```
