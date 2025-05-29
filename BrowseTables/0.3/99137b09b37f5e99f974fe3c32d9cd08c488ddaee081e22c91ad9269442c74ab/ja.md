```julia
open_html_table(table; filename, kwargs...)

```

`table`を`filename`に書き込み（デフォルトでは一時ファイルが生成されます）、その後、デフォルトのアプリケーション（ブラウザであることを願っています）を使用して開きます。キーワード引数は[`write_html_table`](@ref)に渡されます。
