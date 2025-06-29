```
runtests(; options=nothing, ignore_commandline=false)
```

テストスイートを実行します。

この関数にはいくつかの副作用があります：

  * コマンドライン引数を解析し、それを使用して実行オプションの辞書を構築します（リストについてはマニュアルの[実行オプション](@ref run_options_manual)を参照してください）；
  * オプションに従って選択されたテストファイルを取得し、含めます。

`options`は、上記のリストのいくつかのオプションに対応するキーを持つ辞書でなければなりません。`options`が指定されている場合、コマンドライン引数は解析されません。

`ignore_commandline`が`true`の場合、プログラムに渡されたコマンドライン引数は使用されません。このオプションは、使用される実行オプションが呼び出しで指定されたものと正確に一致することを確認したい場合に便利です。

失敗したテストがない場合は`0`を返し、そうでない場合は`1`を返します。
