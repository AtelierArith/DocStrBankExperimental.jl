@wrapmodule libraryfile_cb [functionname]

このマクロ呼び出しを囲むモジュールにC++ライブラリからの関数と型を配置します。別の名前が第二引数として指定されていない限り、`define_julia_module`というエントリポイントを呼び出します。

`libraryfile_cb`は、読み込む共有ライブラリファイルを文字列として返す関数です。JLLが`libfoo.so`をエクスポートしている場合、`foo_jll.get_libfoo_path()`を使用することができます。
