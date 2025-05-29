```julia
optimize(
;
    prerender,
    minify,
    sig,
    prepath,
    no_fail_prerender,
    suppress_errors,
    cleanup
)

```

完全なパスを実行した後、プリレンダリングとミニファイのステップを行います。

  * `prerender=true`: katexとhighlight.jsをプリレンダリングするかどうか（`node.js`が必要）
  * `minify=true`:    出力をミニファイするかどうか（`python3`と`css_html_js_minify`が必要）
  * `sig=false`:      成功を示す整数を返すかどうか（[`publish`](@ref）を参照）
  * `prepath=""`:     プロジェクトページの場合は「project-name」のようなものに設定
  * `no_fail_prerender=true`:  プリレンダリングプロセス中のエラーを無視するかどうか
  * `suppress_errors=true`:    エラーを抑制するかどうか
  * `cleanup=true`:   環境辞書を空にするかどうか

注意: プリレンダリングが`true`に設定されている場合、HTMLファイルが大きくなるため、ミニファイには時間がかかります（特にページに多くの数学がある場合）。
