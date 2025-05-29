```
ensembleaverage(sm::AbstractScatteringModel, imap::IntensityMap; νref=c_cgs, use_approx=true)
```

入力された強度マップ `imap` のアンサンブル平均画像を散乱モデル `sm` を使用して計算します。画像の周波数がメタデータに存在する場合、それを使用して散乱カーネルを計算します。そうでない場合は `νref` を使用して散乱カーネルを計算します。

# 引数

  * `sm::AbstractScatteringModel`: 散乱モデルのインスタンス。
  * `imap::IntensityMap`: 強度マップのインスタンス。
  * `νref::Number=c_cgs`: 散乱カーネルを計算するためのHz単位の周波数。
  * `use_approx::Bool=true`: trueの場合、散乱カーネルを計算するために近似解析式が使用されます。そうでない場合は半解析式が使用されます。
