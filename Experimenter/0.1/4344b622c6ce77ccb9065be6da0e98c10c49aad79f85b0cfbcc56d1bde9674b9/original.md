```
get_global_store()
```

Tries to get the global store that is initialised by the supplied function with the name specified by `init_store_function_name` set in  the running experiment. This store is local to each worker.

# Setup

To create the store, add a function in your include file which returns a dictionary of type Dict{Symbol, Any}, which has the signature similar to:

```julia
function create_global_store(config)
    # config is the global configuration given to the experiment
    data = Dict{Symbol, Any}(
        :dataset => rand(1000),
        :flag => false,
        # etc...
    )
    return data
end
```

Inside your main experiment execution function, you can get this store via `get_global_store`, which is exported by `Experimenter`.

```julia
function myrunner(config, trial_id)
    store = get_global_store()
    dataset = store[:dataset] # Retrieve the keys from the store
    # process data
    return results
end
```
