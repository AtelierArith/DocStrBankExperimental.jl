```
load_results(bids_root::String;
    derivatives_subfolder::String="Unfold",
    lazy::Bool=false,
    generate_Xs::Bool = true,
    ses::Union{Nothing,AbstractString}=nothing,
    task::Union{Nothing,AbstractString}=nothing,
    run::Union{Nothing,AbstractString}=nothing)
```

Load Unfold models existing in a `derivatives_subfolder` in your BIDS root folder. 

# Keywords

  * `derivatives_subfolder::String = "Unfold"`
     Defines in which subfolder of bids_root/derivatives to look for Unfold models.
  * `lazy::Bool = false`
     Do not actually load the dataset into memore if true, only return a dataframe with paths
  * `generate_Xs::Bool = true`
     By default recreate the designmatrix; Can be set to false, to improve loading time.
  * `ses::Union{Nothing,AbstractString} = nothing`
     Which session to load; loads all if nothing
  * `task::Union{Nothing,AbstractString} = nothing`
     Which task to load; loads all if nothing
  * `run::Union{Nothing,AbstractString} = nothing`
     Which run to load; loads all if nothing
