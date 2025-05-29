```
ToggleMenuMaker(header, settings, icons, pagesize=15; kwargs...)
```

`ToggleMenu`の定義値を持つテンプレートを作成します。これは、さらなる引数を使って呼び出すことができます。

# 引数

  * `header`: ユーザーにオプションの機能を知らせる`AbstractString`、または`header(m::ToggleMenu)::String`という関数。
  * `settings`: ユニークで、タイプしやすい必要がある`Vector{Char}`。設定のいずれかに対応するキーを押すと、そのオプションが直接その設定に切り替わります。
  * `icons`: オプションの`Vector{Char}`または`Vector{String}`。提供される場合、これもユニークで、`settings`と同じ数の要素を持つ必要があります。これらは選択アイコンとして使用され、提供されない場合は`settings`がデフォルトとして使用されます。
  * `pagesize`: スクロールする前に表示するオプションの数。

# キーワード引数

  * `braces`: これは文字列または文字のタプルであり、デフォルトは`("[", "]")`です。
  * `keypress`: キーが押されたときに実行される2番目の関数で、標準入力が処理されない場合のみ呼び出されます。シグネチャは`(menu::ToggleMenu, i::UInt32)`で、`i`は入力された文字の少し変わった表現で、[REPL.TerminalMenus](@extref `Menus`)によって提供されます。メニューが完了していない限り、`false`を返すべきで、完了している場合は`true`を返します。

他のキーワード引数は[`TerminalMenus.Config`](@extref `REPL.TerminalMenus.Config`)に渡され、メニューの表示や動作の設定に使用される可能性があります。

`ToggleMenuMaker`は[`ToggleMenu`](@ref)を生成するために呼び出すことができます。
