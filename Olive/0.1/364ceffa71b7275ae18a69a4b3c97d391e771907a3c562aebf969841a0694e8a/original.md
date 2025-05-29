```julia
build(c::Connection, env::Environment{<:Any}; icon::AbstractComponent = olive_loadicon(), sheet::AbstractComponent = DEFAULT_SHEET, 
    themes_enabled::Bool = true) -> Tuple{Component, Component, Component}
```

The `build` function for an `Olive` `Environment` assembles the various components  which compose `Olive` into the `Olive` page. That being said, simply changing the loaded  environment can alter how `Olive` loads entirely. This function should return 

1. the main body from which the `Olive` is built
2. the loadicondiv, the loadicon loaded into a `Component{:div}`. The loadicon can be whatever you want,

and can be provided as an argument to the default `Environment` `build` function. The calling of this function is done on a `Toolips.Route`, we are able to assemble our own `Environment` (`?(Environment)`) or use      `load_default_project!(::Connection)`.

```example
myr = route("/") do c::Connection
    uname = Olive.verify_client!(c)
    # check for environment, if none, we load the default.
    envsearch = findfirst(e::Environment -> e.name == uname, c[:OliveCore].open)
    if isnothing(envsearch)
        env::Environment = load_default_project!(c)
    else
        env = c[:OliveCore].open[getname(c)]
    end
    # setup base UI
    bod::Component{:body}, loadicondiv::Component{:div}, olmod::Module = build(c, env)
end
```

From here, we would still need to load the projects from our `Environment` into our olive main. For reference, this is how `session` does this.

```julia
script!(c, "load", ["olivemain"], type = "Timeout", time = 350) do cm::ComponentModifier
    load_extensions!(c, cm, olmod)
    style!(cm, "loaddiv", "opacity" => 0percent)
    next!(c, loadicondiv, cm, ["olivemain"]) do cm2::ComponentModifier
        remove!(cm2, "loaddiv")
        switch_work_dir!(c, cm2, env.pwd)
        [begin
            append!(cm2, "pane_$(proj.data[:pane])_tabs", build_tab(c, proj))
            if proj.id != env.projects[1].id
                style_tab_closed!(cm2, proj)
            end
        end for proj in env.projects]
        if length(env.projects) > 0
            window::Component{:div} = olmod.build(c, cm2, env.projects[1])
            append!(cm2, "pane_$(env.projects[1].data[:pane])", window)
            focus!(cm2, "cell$(env.projects[1].data[:cells][1].id)")
            p2i = findfirst(proj -> proj[:pane] == "two", env.projects)
            if ~(isnothing(p2i))
                style!(cm2, "pane_container_two", "width" => 100percent, "opacity" => 100percent)
                append!(cm2,"pane_two", olmod.build(c, cm2, env.projects[1]))
            end
        end
    end
end
write!(c, bod)
```

To extend, we start by creating a new symbolic dispatch, this one I am naming `customenv`

```example
import Olive: build
using Olive

function build(c::Connection, env::Environment{:customenv})
    ui_explorer::Component{:div} = projectexplorer()
    ui_explorer[:children] = Vector{Servable}([begin
        olmod.build(c, d)
    end for d in env.directories])
    olivemain::Component{:div} = olive_main()
    olivemain["pane"] = "1"
    pane_one::Component{:section} = section("pane_one")
    pane_one_tabs::Component{:div} = div("pane_one_tabs")
    ...
end
```

From here, we would need to build out the **entire** `Olive` UI. That being said,  `Environment` extensions are likely the least approachable extensions, and it might be valuable  to look at this Function (line 274 of Olive.jl) to get an idea of how it works, and how one might  extend `Olive` using a new `Environment` type.

  * See also: `Project`, `Environment`, `make_session`, `start`, `getname`
