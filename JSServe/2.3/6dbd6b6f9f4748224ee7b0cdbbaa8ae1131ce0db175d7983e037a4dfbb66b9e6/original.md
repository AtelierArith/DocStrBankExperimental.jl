```
Page(;
    offline=false, exportable=true,
    connection::Union{Nothing, FrontendConnection}=nothing,
    server_config...
)
```

A Page can be used for resetting the JSServe state in a multi page display outputs, like it's the case for Pluto/IJulia/Documenter. For Documenter, the page needs to be set to `exportable=true, offline=true`, but doesn't need to, since Page defaults to the most common parameters for known Packages. Exportable has the effect of inlining all data & js dependencies, so that everything can be loaded in a single HTML object. `offline=true` will make the Page not even try to connect to a running Julia process, which makes sense for the kind of static export we do in Documenter. For convenience, one can also pass additional server configurations, which will directly get put into `configure_server!(;server_config...)`. Have a look at the docs for `configure_server!` to see the parameters.
