```
AnalysisMethod(
    conctable::AbstractDataTable, 
    signaltable::Union{AbstractDataTable, Nothing}, 
    signal, 
    pointlevel = Int[]; 
    signal = :area, 
    rel_sig = :relative_signal, 
    est_conc = :estimated_concentration, 
    true_conc = :true_concentration, 
    kwargs...
)
```

`AnalysisMethod`の便利なコンストラクタで、`Table`の構築をオプションにします。

定量化のための`signal`データ型。`levelname`は`pointlevel`の列名です。他の引数の詳細については`AnalysisMethod`を参照してください。

# キーワード引数

  * `rel_sig`: 相対信号のキー名。
  * `est_conc`: 推定濃度のキー名。
  * `true_conc`: 真の濃度のキー名。
  * `acc`: 精度のキー名。
  * その他のキーワード引数は`analytetable`の列になります。`analyte`、`isd`、および`calibration`が提供されていない場合、`conctable`のanalyteが使用されます。
