```
PressureVariable(
    ST = String;
    ID :: AbstractString,
    long :: AbstractString = "",
    name :: AbstractString,
    units :: AbstractString,
    hPa   :: Int = 0,
    throw :: Bool = true
) -> evar :: PressureCustom
```

デフォルトのリストに含まれていないカスタム圧力レベル変数を作成します。これらの変数はCDSストアでは利用できないため、他の変数から別途計算して分析する必要があります。

# キーワード引数

  * `ID` : NetCDFファイルで使用される変数ID（文字列形式）
  * `long` : 変数の長い名前（CDSダウンロード用の変数を指定する際に使用）
  * `name` : ユーザー定義の変数名
  * `units` : ユーザー定義の変数の単位
  * `hPa`   : hPaで指定された圧力レベル。デフォルトは0で、すべてのレベルを示します。
  * `throw` : `hPa`レベルが存在しない場合、`throw`がtrueであればエラーを投げ、それ以外の場合は最も近い圧力レベルを見つけます。
