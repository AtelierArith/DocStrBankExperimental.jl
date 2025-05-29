```
export_static(html_file::Union{IO, String}, app::App)
export_static(folder::String, routes::Routes)
```

`app`で定義されたアプリとそのすべてのアセットを単一のHTMLファイルとしてエクスポートします。または、`routes`で定義されたすべてのルートを`folder`にエクスポートします。
