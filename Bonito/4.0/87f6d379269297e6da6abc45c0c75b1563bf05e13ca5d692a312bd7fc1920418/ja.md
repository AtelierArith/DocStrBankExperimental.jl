```
interactive_server(f, paths, modules=[]; url="127.0.0.1", port=8081, all=true)
```

Bonitoに基づいて静的サイトを提供し、コードの変更があるたびに更新されるベースサーバーを改訂します！

使用法：

```julia
using Revise, Website
using Website.Bonito

# インタラクティブサーバーを起動し、ウェブサイトを開発しましょう！
routes, task, server = interactive_server(Website.asset_paths()) do
    return Routes(
        "/" => App(index, title="Makie"),
        "/team" => App(team, title="Team"),
        "/contact" => App(contact, title="Contact"),
        "/support" => App(support, title="Support")
    )
end

# すべてが良さそうなら、静的サイトをエクスポートします
dir = joinpath(@__DIR__, "docs")
# bonitoによって生成されたファイルのみ削除します
rm(joinpath(dir, "bonito"); recursive=true, force=true)
Bonito.export_static(dir, routes)
```

完全なコードについては、Bonitoを使用しているMakieウェブサイトリポジトリを訪れてください: [MakieOrg/Website](https://github.com/MakieOrg/Website/blob/sd/bonito/make.jl)
