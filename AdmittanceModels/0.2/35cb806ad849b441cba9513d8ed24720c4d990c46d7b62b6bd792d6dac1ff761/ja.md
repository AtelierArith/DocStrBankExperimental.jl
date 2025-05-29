```
Circuit(q3d_file; matrix_types = [:capacitance])
```

ANSYS Q3Dによって生成されたRLGCシミュレーション出力を含むプレーンテキストファイルから`AdmittanceModels.Circuit`を返します。

# 引数

  * `q3d_file`: テキストファイルへのパス。
  * `matrix_type`: 読み取るマトリックスデータのタイプを示すシンボルのリスト。現在、[:capacitance, :conductance]のシンボルのみが利用可能な選択肢であり、["pF", "nF", "mF", "uF", "fF", "farad", "sie", "mSie"]の単位のみが処理されます。
