```
# 単一の式/ステートメントを解析する
parsestmt(TreeType, text, [index];
          version=VERSION,
          ignore_trivia=true,
          filename=nothing,
          ignore_errors=false,
          ignore_warnings=ignore_errors)

# トップレベル（ファイルスコープ）ですべてのステートメントを解析する
parseall(...)

# 単一の構文原子を解析する
parseatom(...)
```

Juliaソースコード文字列`text`を`TreeType`型のデータ構造に変換します。`parsestmt`は単一のJuliaステートメントを解析し、`parseall`はファイルスコープでトップレベルのステートメントを解析し、`parseatom`は単一のJulia識別子または他の「構文原子」を解析します。

`index`なしで`text`が渡されると、すべての入力テキストが消費され、ツリーデータ構造が返されます。整数バイト`index`が渡されると、次のインデックスを含むタプル`(tree, next_index)`が返され、`text`の解析を再開するための次のインデックスが含まれます。デフォルトでは、有効なコードの前後の空白とコメントは無視されますが、`ignore_trivia=false`を設定することでこれをオフにすることができます。

`version`（デフォルトは`VERSION`）は、構文バージョンを任意のJuliaバージョン`>= v"1.0"`に設定するために使用できます。私たちは、v"1.0"以降に追加されたすべてのJulia構文を解析することを目指しており、要求された`version`と互換性がない場合はエラーを出力します。

`filename`を渡すことで、出力ツリー内に埋め込まれたファイル名情報を設定できます。これにより、エラーや警告にソースファイル名が注釈されます。

解析中にエラーや警告が発生した場合、`ParseError`がスローされます。警告による例外を回避するには、`ignore_warnings=true`を使用します。エラーによる例外も回避するには、`ignore_errors=true`を使用します。
