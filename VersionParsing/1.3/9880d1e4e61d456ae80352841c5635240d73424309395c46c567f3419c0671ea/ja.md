`VersionParsing` パッケージは、`vparse(string)` 関数を介して、バージョン番号文字列を Julia の組み込み `VersionNumber` 型に柔軟に解析する機能を実装しています。

`VersionNumber(string)` コンストラクタとは異なり、`vparse(string)` は例外をスローすることなく、はるかに広範囲の形式のバージョン番号文字列を処理できます。
