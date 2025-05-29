```
@stipple_precompile(setup, workload)
```

Stipple関連のコードのプリコンパイルプロセスを容易にするマクロです。

# 引数

  * `setup`: プリコンパイルに必要なオプションのセットアップ構成。
  * `workload`: プリコンパイルする必要がある作業負荷またはタスク。

このマクロは、`precompile_get`、`precompile_post`、および `precompile_request` の3つのローカルルーチンを定義します。これらのルーチンは、プリコンパイルプロセス中に開始されるローカルサーバーにリクエストを送信するために使用できます。

環境変数 ENV["STIPPLE*PRECOMPILE*REQUESTS"] を "false" に設定すると、HTTP.requests のプリコンパイルを無効にできます。デフォルト値は "true" です。

# 例（Stipple.jlの最後も参照）

```
module MyApp
using Stipple, Stipple.ReactiveTools

@app PrecompileApp begin
    @in demo_i = 1
    @out demo_s = "Hi"

    @onchange demo_i begin
    println(demo_i)
    end
end

ui() = [cell("hello"), row("world"), htmldiv("Hello World")]

function __init__()
    @page("/", ui)
end

@stipple_precompile begin
    # @page マクロはここで呼び出すことはできません。なぜなら、ディスクにキャッシュファイルを書き込むことに依存しているからです。
    # したがって、プリコンパイルのために手動のルート定義を使用します。

    route("/") do
        model = @init PrecompileApp
        page(model, ui) |> html
    end

    precompile_get("/")
end

end
```
