```
fitdiscrete(net, model, tipdata)
fitdiscrete(net, model, RateVariationAcrossSites, tipdata)
fitdiscrete(net, model, species, traits)
fitdiscrete(net, model, RateVariationAcrossSites, species, traits)
fitdiscrete(net, model, dnadata, dnapatternweights)
fitdiscrete(net, model, RateVariationAcrossSites, dnadata, dnapatternweights)
fitdiscrete(net, modSymbol, species, traits)
fitdiscrete(net, modSymbol, dnadata, dnapatternweights)
```

Calculate the maximum likelihood (ML) score of a network or tree given one or more discrete characters at the tips. Along each edge, transitions are modelled with a continous time Markov `model`, whose parameters are estimated (by maximizing the likelihood). At each hybrid node, the trait is assumed to be inherited from either of the two immediate parents according to the parents' average genetic contributions (inheritance γ). The model ignores incomplete lineage sorting. The algorithm extracts all trees displayed in the network.

Data can given in one of the following:

  * `tipdata`: dictionary taxon => state label, for a single trait.
  * `tipdata`: data frame for a single trait, in which case the taxon names are to appear in column 1 or in a column named "taxon" or "species", and trait *labels* are to appear in column 2 or in a column named "trait". Here, trait labels should be as they appear in `getlabels(model)`.
  * `species`: vector of strings, and `traits`: DataFrame of traits, with rows in the order corresponding to the order of species names. Again, trait labels should be as they appear in `getlabels(model)`. All traits are assumed to follow the same model, with same parameters.
  * `dnadata`: the first part of the output of readfastatodna, a dataframe of BioSequence DNA sequences, with taxon in column 1 and a column for each site.
  * `dnapatternweights`: the second part of the output of readfastatodna, an array of weights, one weights for each of the site columns. The length of the weight is equal to nsites. If using dnapatternweights, must provide dnadata.
  * RateVariationAcrossSites: model for rate variation (optional)

Optional arguments (default):

  * `optimizeQ` (true): should model rate parameters be fixed, or should they be optimized?
  * `optimizeRVAS` (true): should the model optimize the parameters for the variability of rates across sites (α and/or p_invariable)?
  * `NLoptMethod` (`:LN_COBYLA`, derivative-free) for the optimization algorithm. For other options, see the [NLopt](https://nlopt.readthedocs.io/en/latest/NLopt_Algorithms/).
  * tolerance values to control when the optimization is stopped: `ftolRel` (1e-12), `ftolAbs` (1e-10) on the likelihood, and `xtolRel` (1e-10), `xtolAbs` (1e-10) on the model parameters.
  * bounds for the alpha parameter of the Gamma distribution of rates across sites: `alphamin=0.05`, `alphamax=50`.
  * `verbose` (false): if true, more information is output.
  * `suppresswarnings` (false): if true, warnings from [`check_matchtaxonnames!`](@ref) are suppressed.

# examples:

```jldoctest fitDiscrete_block
julia> net = readnewick("(((A:2.0,(B:1.0)#H1:0.1::0.9):1.5,(C:0.6,#H1:1.0::0.1):1.0):0.5,D:2.0);");

julia> m1 = BinaryTraitSubstitutionModel([0.1, 0.1], ["lo", "hi"]);

julia> using DataFrames

julia> dat = DataFrame(species=["C","A","B","D"], trait=["hi","lo","lo","hi"]);

julia> fit1 = fitdiscrete(net, m1, dat)
PhyloTraits.StatisticalSubstitutionModel:
Binary Trait Substitution Model:
  rate lo→hi α=0.27222
  rate hi→lo β=0.34981
on a network with 1 reticulations
data:
  4 species
  1 trait
log-likelihood: -2.7277

julia> tips = Dict("A" => "lo", "B" => "lo", "C" => "hi", "D" => "hi");

julia> fit2 = fitdiscrete(net, m1, tips; xtolRel=1e-16, xtolAbs=1e-16, ftolRel=1e-16)
PhyloTraits.StatisticalSubstitutionModel:
Binary Trait Substitution Model:
  rate lo→hi α=0.27222
  rate hi→lo β=0.34981
on a network with 1 reticulations
data:
  4 species
  1 trait
log-likelihood: -2.7277
```

Note that a copy of the network is stored in the fitted object, but the internal representation of the network may be different in `fit1.net` and in the original network `net`:

```jldoctest fitDiscrete_block
julia> net = readnewick("(sp1:3.0,(sp2:2.0,(sp3:1.0,sp4:1.0):1.0):1.0);");

julia> using BioSymbols

julia> tips = Dict("sp1" => BioSymbols.DNA_A, "sp2" => BioSymbols.DNA_A, "sp3" => BioSymbols.DNA_G, "sp4" => BioSymbols.DNA_G);

julia> mJC69 = JC69([0.25], false);

julia> fitJC69 = fitdiscrete(net, mJC69, tips)
PhyloTraits.StatisticalSubstitutionModel:
Jukes and Cantor 69 Substitution Model,
  absolute rate version
  off-diagonal rates equal to 0.29233/3.
  rate matrix Q:
                 A       C       G       T
         A       *  0.0974  0.0974  0.0974
         C  0.0974       *  0.0974  0.0974
         G  0.0974  0.0974       *  0.0974
         T  0.0974  0.0974  0.0974       *
on a network with 0 reticulations
data:
  4 species
  1 trait
log-likelihood: -4.99274

julia> rv = RateVariationAcrossSites(alpha=1.0, ncat=4)
Rate variation across sites: discretized Gamma
alpha: 1.0
categories for Gamma discretization: 4
rates: [0.146, 0.513, 1.071, 2.27]

julia> fitdiscrete(net, mJC69, rv, tips; optimizeQ=false, optimizeRVAS=false)
PhyloTraits.StatisticalSubstitutionModel:
Jukes and Cantor 69 Substitution Model,
  absolute rate version
  off-diagonal rates equal to 0.25/3.
  rate matrix Q:
                 A       C       G       T
         A       *  0.0833  0.0833  0.0833
         C  0.0833       *  0.0833  0.0833
         G  0.0833  0.0833       *  0.0833
         T  0.0833  0.0833  0.0833       *
Rate variation across sites: discretized Gamma
  alpha: 1.0
  categories for Gamma discretization: 4
  rates: [0.146, 0.513, 1.071, 2.27]
on a network with 0 reticulations
data:
  4 species
  1 trait
log-likelihood: -5.2568

```

fixit: add option to allow users to specify root prior, using either equal frequencies or stationary frequencies for trait models.
