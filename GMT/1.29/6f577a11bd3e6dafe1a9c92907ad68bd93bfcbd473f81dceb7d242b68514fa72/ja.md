```
mblevitus(cmd0::String=""; kwargs...)
```

指定された1度×1度の地域の平均年間水柱を代表する水の速度プロファイルを作成します。

## パラメータ

  * **A** | **all4** :: [Type => Bool]

    深さ、速度、温度、塩分も含む。
  * **L** | **location** :: [Type => Str | Tuple]		$Arg = lon/lat$

    水の速度プロファイルの位置の経度と緯度を設定します。
  * **O** | **outfile** | **out_file** :: [Type => Str]

    SVPを<outfile>に書き込みます。
  * **H** | **help** :: [Type => Bool]

    プログラムの説明を出力します。
  * **z** | **z_down** :: [Type => Bool]

    Z軸を下向きに正にします（ここでのデフォルトはZ上向きです）。
  * **V** | **verbose** :: [Type => Bool or Str]		$Arg = [level]$

    進行状況レポートをstderrに送信する冗長性レベルを選択します。
