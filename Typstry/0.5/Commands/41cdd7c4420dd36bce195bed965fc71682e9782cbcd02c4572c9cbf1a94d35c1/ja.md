```
typst(::AbstractString; catch_interrupt = true, ignorestatus = true)
```

インタラクティブな使用を目的とした便利な関数で、typstコマンドラインインターフェースをエミュレートします。ただし、スペースで厳密に分割され、シェルスタイルのエスケープメカニズムは提供されないため、スペースを含むファイル名がある場合などには機能しません。

`catch_interrupt`がtrueの場合、CTRL-Cはコマンドを静かに終了します。[`ignorestatus`](@ref)がtrueの場合、Typstの失敗はjuliaエラーを意味しません。

`"TYPST_FONT_PATHS"`環境変数が設定されていない場合、一時的に[`julia_mono`](@ref)に設定されます。
