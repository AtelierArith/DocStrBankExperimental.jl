```
interactive_server(f, paths, modules=[]; url="127.0.0.1", port=8081, all=true)
```

Revise base server that will serve a static side based on Bonito and will update on any code change!

Usage:

```julia
using Revise, Website
using Website.Bonito

# Start the interactive server and develop your website!
routes, task, server = interactive_server(Website.asset_paths()) do
    return Routes(
        "/" => App(index, title="Makie"),
        "/team" => App(team, title="Team"),
        "/contact" => App(contact, title="Contact"),
        "/support" => App(support, title="Support")
    )
end

# Once everything looks good, export the static site
dir = joinpath(@__DIR__, "docs")
# only delete the bonito generated files
rm(joinpath(dir, "bonito"); recursive=true, force=true)
Bonito.export_static(dir, routes)
```

For the complete code, visit the Makie website repository which is using Bonito: [MakieOrg/Website](https://github.com/MakieOrg/Website/blob/sd/bonito/make.jl)
