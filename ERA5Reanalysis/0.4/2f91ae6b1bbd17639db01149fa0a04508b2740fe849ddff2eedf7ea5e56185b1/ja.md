```
SingleVariable(
    ST = String;
    ID :: AbstractString,
    long :: AbstractString = "",
    name :: AbstractString,
    units :: AbstractString
) -> evar :: SingleLevel
```

カスタムシングルレベル変数を作成します。これはERA5Reanalysis.jlによってエクスポートされるデフォルトリストには含まれていません。これらの変数はCDSストアでは利用できないため、他の変数から別途計算し、分析する必要があります。

# キーワード引数

  * `ID` : NetCDFファイルで使用される変数ID（文字列形式）
  * `long` : 変数のロングネーム（CDSダウンロード用の変数を指定する際に使用）
  * `name` : ユーザー定義の変数名
  * `units` : ユーザー定義の変数の単位
  * `inCDS` : この変数がCDSストアで利用可能かどうかを示すブール値。利用可能な場合はTrue。
