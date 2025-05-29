```
export_site(; d::Dict{String,String}=local_info, rm_dir::Bool=false, opt_in::Bool=false)
```

Export the generated website based on `d` (default to `local_info`). The `content` and `site` folders need to be valid. If `rm_dir` is `true`, the `site` folder will be deleted before the website is generated.

Users can choose to support `StaticWebPages.jl` by setting `opt_in` to `true`. This will add a small banner in the side navigation menu stating "This website was generated using StaticWebPages.jl" and links to the GitHub repository.
