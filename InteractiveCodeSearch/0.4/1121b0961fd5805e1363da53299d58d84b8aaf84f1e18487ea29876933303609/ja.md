# InteractiveCodeSearch.jl –– インタラクティブにJuliaコードを検索

Juliaには、関数の実装を読むために非常に便利な`@edit`、`@less`などがあります。しかし、コードの場所を見つけるためには「十分に良い」(型)パラメータのセットを指定する必要があります。

その代わりに、`InteractiveCodeSearch`は、読みたいコードをインタラクティブに選択するためのいくつかのマクロを提供します。

## 機能

  * コードの場所をエディタで開く前に、メソッドシグネチャをインタラクティブに選択できます。
  * メソッドを検索するためのさまざまな方法があります。例えば：関数名による`@search show`、関数呼び出し式による`@search show(stdout, "hello")`、関数呼び出しシグネチャによる`@search show(::IO, ::String)`、モジュール名による`@search Base`、引数値による`@searchmethods 1`、および引数型による`@searchmethods ::Int`。
  * インタラクティブな検索履歴。IJuliaでも動作します。

## 例

```julia
using InteractiveCodeSearch
@search show             # メソッド定義を検索
@searchmethods 1         # 整数に対して定義されたメソッドを検索
@searchhistory           # 検索履歴 (Julia ≥ 0.7)
```

## 要件

  * インタラクティブなマッチングコマンド。例えば：

      * [fzf](https://github.com/junegunn/fzf) (ターミナルのデフォルト)
      * [peco](https://github.com/peco/peco)
      * [percol](https://github.com/mooz/percol)
      * [rofi](https://github.com/DaveDavenport/rofi) (GUI; IJuliaのデフォルト)
