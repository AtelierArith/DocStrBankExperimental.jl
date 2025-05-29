`StripRTF`モジュールは、文字列からすべてのフォーマットを削除して「プレーンテキスト」を生成する単一の関数、[`striprtf(text)`](@ref)をエクスポートします。この文字列は[リッチテキストフォーマット (RTF)](https://en.wikipedia.org/wiki/Rich_Text_Format)です。

このコードは、Joshy CyriacによるPythonの[`striprtf`パッケージ](https://github.com/joshy/striprtf)のJuliaポートであり、さらにMarkus JarderotとGilson Filhoによって[StackOverflowに投稿されたコード](https://stackoverflow.com/questions/188545/regular-expression-for-extracting-text-from-an-rtf-string)に基づいています。
