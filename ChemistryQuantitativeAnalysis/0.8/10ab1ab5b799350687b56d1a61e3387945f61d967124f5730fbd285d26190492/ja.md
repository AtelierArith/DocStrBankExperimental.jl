```
mkbatch(file::String; 
        delim = '	',
        data_table = SampleDataTable,
        signal_table = SampleDataTable,
        conc_table = SampleDataTable,
        data_config = Dict{Symbol, Any}(), 
        signal_config = Dict{Symbol, Any}(), 
        conc_config = Dict{Symbol, Any}(), 
        method_config = Dict{Symbol, Any}()
        )
```

バッチのテンプレートディレクトリを作成します。設定の利用可能なキーと値については「README.md」を参照してください。

デフォルトのテーブルラッパーは `SampleDataTable` で、デフォルトのサンプル列名は "Sample"、レベルのデフォルトのサンプル列名は "Level" です。`AnalyteDataTable` のデフォルトの分析物列名は "Analyte" です。

デフォルトの分析物の優先順位は `conc_config[:Analyte]`、`signal_config[:Analyte]`、`data_config[:Analyte]`、最後に `["Analyte1", "Analyte2"]` です。データのデフォルトサンプルは `["S1", "S2"]` です。デフォルトのキャリブレーションポイントは `["C1", "C2", "C3", "C4", "C5"]` です。デフォルトのキャリブレーションレベルは `[1, 2, 3, 4, 5]` です。
