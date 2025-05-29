```julia
build(c::Connection, om::OliveModifier, oe::OliveExtension{<:Any}) -> ::Nothing
```

これは基本的な `Olive` 拡張関数で、`load` 拡張を作成するために使用されます。これらは `Olive` の起動時に何かを行う拡張です。`build` を拡張するには、`import` で `build` をインポートし、新しい `Method` を記述します。

```example
import Olive: build
using Olive
using ToolipsSession: alert!

build(c::Connection, om::OliveModifier, oe::OliveExtension{:hello}) = begin
    olive_notify!(om, "hello !", color = "darkgreen")
end
```

以下の例は `OliveDocBrowser` から抜粋したものです：

```example
import Olive: build
using Olive
using Olive.Toolips
using Olive.ToolipsSession

build(c::Connection, om::OliveModifier, oe::OliveExtension{:docbrowser}) = begin
    explorericon = topbar_icon("docico", "newspaper")
    on(c, explorericon, "click") do cm::ComponentModifier
        mods = [begin 
            if :mod in keys(p.data)
                p.data[:mod]
            else
                nothing
            end
        end for p in c[:OliveCore].open[getname(c)].projects]
        filter!(x::Any -> ~(isnothing(x)), mods)
        push!(mods, Olive, olive)
        cells = Vector{Cell}([Cell(e, "docmodule", "", mod) for (e, mod) in enumerate(mods)])
        home_direc = Directory(c[:OliveCore].data["home"])
        projdict::Dict{Symbol, Any} = Dict{Symbol, Any}(:cells => cells,
        :path => home_direc.uri, :env => home_direc.uri)
        myproj::Project{:doc} = Project{:doc}(home_direc.uri, projdict)
        push!(c[:OliveCore].open[getname(c)].projects, myproj)
        tab::Component{:div} = build_tab(c, "documentation")
        open_project(c, om, proj, tab)
    end
    insert!(om, "rightmenu", 1, explorericon)
end
```
