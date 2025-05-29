```
scrape_operas(base_urls::Vector{String};
              pages::Integer = 1,
              save_to::Union{Nothing,AbstractString} = nothing)
```

Fetch metadata for operas listed under each URL in `base_urls`, iterating pages 1 through `pages`. Returns a DataFrame with columns:

• Opera*Name     • Premiere*Date     • Composer     • Librettist*Literary*Source     • Genre     • City     • State_Region     • Country     • Theater  

If `save_to` is a file path (e.g. `"data/italy.csv"`), the DataFrame is also written to that CSV before being returned.
