```
export_site(; d::Dict{String,String}=local_info, rm_dir::Bool=false, opt_in::Bool=false)
```

`d`に基づいて生成されたウェブサイトをエクスポートします（デフォルトは`local_info`）。`content`および`site`フォルダーは有効である必要があります。`rm_dir`が`true`の場合、ウェブサイトが生成される前に`site`フォルダーは削除されます。

ユーザーは`opt_in`を`true`に設定することで`StaticWebPages.jl`をサポートすることを選択できます。これにより、サイドナビゲーションメニューに「このウェブサイトはStaticWebPages.jlを使用して生成されました」という小さなバナーが追加され、GitHubリポジトリへのリンクが表示されます。
