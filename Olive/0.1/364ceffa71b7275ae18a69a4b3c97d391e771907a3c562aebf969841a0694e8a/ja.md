```julia
build(c::Connection, env::Environment{<:Any}; icon::AbstractComponent = olive_loadicon(), sheet::AbstractComponent = DEFAULT_SHEET, 
    themes_enabled::Bool = true) -> Tuple{Component, Component, Component}
```

`Olive` `Environment`のための`build`関数は、`Olive`を構成するさまざまなコンポーネントを`Olive`ページに組み立てます。言い換えれば、読み込まれる環境を変更するだけで、`Olive`の読み込み方法が完全に変わる可能性があります。この関数は次のものを返す必要があります。

1. `Olive`が構築されるメインボディ
2. `Component{:div}`に読み込まれたloadiconを持つloadicondiv。loadiconはあなたが望むものであり、

デフォルトの`Environment` `build`関数への引数として提供できます。この関数の呼び出しは`Toolips.Route`上で行われ、独自の`Environment`（`?(Environment)`）を組み立てるか、`load_default_project!(::Connection)`を使用できます。

```example
myr = route("/") do c::Connection
    uname = Olive.verify_client!(c)
    # 環境を確認し、ない場合はデフォルトを読み込みます。
    envsearch = findfirst(e::Environment -> e.name == uname, c[:OliveCore].open)
    if isnothing(envsearch)
        env::Environment = load_default_project!(c)
    else
        env = c[:OliveCore].open[getname(c)]
    end
    # ベースUIを設定
    bod::Component{:body}, loadicondiv::Component{:div}, olmod::Module = build(c, env)
end
```

ここから、`Environment`からプロジェクトを`olive`メインに読み込む必要があります。参考までに、これが`session`がこれを行う方法です。

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

拡張するために、新しいシンボリックディスパッチを作成します。これを`customenv`と名付けます。

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

ここから、**全体の**`Olive` UIを構築する必要があります。言い換えれば、`Environment`拡張はおそらく最もアプローチしにくい拡張であり、この関数（Olive.jlの274行目）を見て、どのように機能するか、そして新しい`Environment`タイプを使用して`Olive`を拡張する方法を理解することが価値があるかもしれません。

  * 参照: `Project`, `Environment`, `make_session`, `start`, `getname`
