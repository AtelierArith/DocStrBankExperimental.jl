```julia
optimize(
;
    prepath,
    version,
    prerender,
    minify,
    sig,
    no_fail_prerender,
    on_write,
    suppress_errors,
    clear,
    cleanup,
    fail_on_warning
)

```

完全なパスを実行した後、プレレンダリングとミニファイステップを行います。

  * `prepath=""`:     プロジェクトページの場合は「project-name」のように設定します（通常、これはconfig.mdを介して設定されます）
  * `version=""`:     「dev」の場合、基本URLは`/{prepath}/dev/`になります。「xxx」の場合、基本URLは`/{prepath}/stable/`になり、ウェブサイトのコピーも`/{prepath}/xxx/`に作成されます。例として`version="v0.15.2"`があります。空のままにすると、基本URLは単に`/{prepath}/`になります。
  * `is_preview=false`: trueの場合、指定されたバージョンに関係なく、`/stable/`と`/dev/`は更新されません。
  * `prerender=true`: katexとhighlight.jsをプレレンダリングするかどうか（`node.js`が必要）
  * `minify=true`:    出力をミニファイするかどうか（`python3`と`css_html_js_minify`が必要）
  * `sig=false`:      成功を示す整数を返すかどうか（[`publish`](@ref)を参照）
  * `clear=false`:    出力ディレクトリをクリアしてすべてを再生成するかどうか
  * `no_fail_prerender=true`: プレレンダリングプロセス中のエラーを無視するかどうか
  * `suppress_errors=true`:   エラーを抑制するかどうか
  * `fail_on_warning=false`:   trueの場合、警告は致命的なエラーになります
  * `cleanup=true`:   環境辞書を空にするかどうか
  * `on_write(pg, fd_vars)`: ページがレンダリングされた後のコールバック関数で、レンダリングされたページとページ変数を引数として渡します

注意: プレレンダリングが`true`に設定されている場合、HTMLファイルが大きくなるため、ミニファイには時間がかかります（特にページに多くの数学がある場合）。
