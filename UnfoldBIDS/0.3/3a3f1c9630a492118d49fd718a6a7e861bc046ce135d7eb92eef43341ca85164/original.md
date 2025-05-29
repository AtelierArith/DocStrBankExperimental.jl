```
bids_layout(bidsPath::AbstractString;
    derivatives::Bool=true,
    specific_folder::Union{Nothing,AbstractString}=nothing,
    exclude_folder::Union{Nothing,AbstractString}=nothing,
    ses::Union{Nothing,AbstractString}=nothing,
    task::Union{Nothing,AbstractString}=nothing,
    run::Union{Nothing,AbstractString}=nothing)
```

Main function to load paths of all subjects in one `bids_root` folder. Will return a DataFrame containing all found paths with specific subject information. Used before loading data into memore using [`load_bids_eeg_data`](@ref)

## Keywords

  * `derivatives::Bool = true`
     Look for data in the derivatives folder
  * `specific_folder::Union{Nothing,AbstractString} = nothing`
     Specify a specific folder name in either derivatives or bids_root to look for data.
  * `exclude_folder::Union{Nothing,AbstractString} = nothing`
     Exclude a specific folder from data detection.
  * `ses:Union{Nothing,AbstractString} = nothing`
     Which session to load; loads all if nothing
  * `task::Union{Nothing,AbstractString} = nothing`
     Which task to load; loads all if nothing
  * `run::Union{Nothing,AbstractString} = nothing`
     Which run to load; loads all if nothing
