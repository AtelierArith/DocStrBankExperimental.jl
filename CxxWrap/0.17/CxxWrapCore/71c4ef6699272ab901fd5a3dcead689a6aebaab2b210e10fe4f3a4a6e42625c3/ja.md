@readmodule libraryfile_cb [functionname]

C++モジュールを読み込み、マクロ呼び出しを囲むJuliaモジュールに関連付けます。 `libraryfile_cb`は、読み込む共有ライブラリファイルを文字列として返す関数です。JLLが`libfoo.so`をエクスポートしている場合、`foo_jll.get_libfoo_path()`を使用することができます。
