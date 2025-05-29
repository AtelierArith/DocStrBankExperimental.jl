```
ensembleaverage(sm::AbstractScatteringModel, skymodel::AbstractModel, νmodel; use_approx=true)
```

入力スカイモデル `skymodel` のアンサンブル平均画像を散乱モデル `sm` を使用して計算します。

# 引数

  * `sm::AbstractScatteringModel`: 散乱モデルのインスタンス。
  * `skymodel::AbstractModel`: `AbstractModel` のインスタンス。
  * `νmodel::Number=c_cgs`: 散乱カーネルを計算するための周波数（Hz）。
  * `use_approx::Bool=true`: true の場合、散乱カーネルを計算するために近似解析式が使用されます。そうでない場合は半解析式が使用されます。
