```
pkplot(data::DataSet{T};
typesort::Union{Nothing, Symbol, AbstractVector{Symbol}} = nothing,
pagesort::Union{Nothing, Symbol, AbstractVector{Symbol}, NoPageSort} = nothing,
filter::Union{Nothing, Dict{Symbol}} = nothing,
uylims::Bool = false,
ldict = nothing,
savepath::Union{Nothing, AbstractString} = nothing,
namepref::Union{Nothing, AbstractString} = nothing,
onlyplots = false,
kwargs...) where T <: AbstractSubject
```

PK plot for subject set.

  * `typesort` - sort on page by this id key;
  * `pagesort` - different pages by this id key;
  * `filter` - use only subjects if filter ⊆ subject id;
  * `uylims` - same ylims for all dataset;
  * `ldict` - Dict with labels for replace;
  * `savepath` - path for plot saving;
  * `namepref` - name prefix for saving files.
  * `onlyplots` - if `true` return only vetor of plots;

Use `pagesort = MetidaNCA.NoPageSort()` to prevent page plotting (return single plot).

Return vector of pairs: `Page ID` => `Plot`.
