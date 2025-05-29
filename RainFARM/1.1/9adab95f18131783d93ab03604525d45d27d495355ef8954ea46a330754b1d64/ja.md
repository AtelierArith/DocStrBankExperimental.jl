```
ww = rfweights(orofile, reffile, nf; weightsfn="", varname="", fsmooth=false)
```

細かいスケールの降水気候ファイルから地形的重みを計算します。

# 引数

  * `orofile`  : 入力気候のファイル名
  * `reffile`  : 参照ファイルのファイル名（メタデータ用、例えばダウンスケールするファイル）
  * `nf`       : 空間ダウンスケーリングのための精緻化係数
  * `weightsfn`: 重みをファイルweightsfnに書き込む
  * `varname`  : 気候の変数名
  * `fsmooth`  : gp保存の代わりにスムージングを使用する

# 戻り値

  * `ww`       : 重み行列、weightsfnにも保存されます

# 依存関係

この関数は、システムに「cdo」コマンド（https://code.mpimet.mpg.de/projects/cdo/wiki/Cdo）が利用可能である必要がある外部システムコールを使用します。
