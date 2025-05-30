```
report_package(package::Module; jetconfigs...) -> JETToplevelResult
report_package(package::AbstractString; jetconfigs...) -> JETToplevelResult
```

`package`を[`report_file`](@ref)と同様に分析し、特別なデフォルト設定で型レベルのエラーを返します。これらの設定は、パッケージを分析するために特に調整されています（詳細は以下を参照）。`package`引数は`Module`または`AbstractString`のいずれかである必要があります。後者の場合、現在の環境におけるパッケージの名前でなければなりません。

この関数によって実行されるエラー分析は、デフォルトで以下のように構成されています：

  * `analyze_from_definitions = true`: これにより、JETはトップレベルの呼び出しサイトなしで分析を開始できます。これは、パッケージ自体が通常、型やメソッドの定義のみを含み、その使用（すなわち呼び出しサイト）は含まないため、パッケージを分析するのに便利です。
  * `concretization_patterns = [:(x_)]`: 指定された`package`内のすべてのトップレベルコードを具体化します。具体化は、成功した分析のために一般的に好まれます。ほとんどの場合、パッケージ内に書かれたトップレベルコードを解釈して具体化するのは安価です。なぜなら、それは通常、型やメソッドのみを定義するからです。
  * `ignore_missing_comparison = true`: JETは、推論が不十分な比較演算子呼び出し（例：`==`）が`missing`を返す可能性を無視します。これは、`report_package`が分析の初めに不十分な入力引数の型情報に依存することが多く、そのためにこのような比較演算子呼び出しの潜在的な`missing`戻り値に基づいてノイズの多いエラーレポートが生成されるため、便利です。ターゲットパッケージが`missing`を処理する必要がある場合、この設定はオフにする必要があります。なぜなら、実行時に実際に発生する可能性のあるエラーを隠すからです。

詳細については、[`ToplevelConfig`](@ref)および[`JETAnalyzer`](@ref)を参照してください。

なお、[一般的な設定](@ref)および[エラー分析特有の設定](@ref jetanalysis-config)はキーワード引数として指定でき、指定された場合は上記のデフォルト設定よりも優先されます。

---

```
report_package(; jetconfigs...) -> JETToplevelResult
```

上記と同様ですが、現在のプロジェクトのパッケージを分析します。

また、[`report_file`](@ref)も参照してください。
