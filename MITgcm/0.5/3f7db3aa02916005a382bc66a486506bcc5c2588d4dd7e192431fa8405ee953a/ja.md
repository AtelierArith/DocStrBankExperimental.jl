```
scan_stdout(filout::String)
```

MITgcmの標準出力テキストファイル（"output.txt"または"STDOUT.0000"）をスキャンし、収集した情報のNamedTupleを返します。

  * packages : コンパイルおよび使用されているパッケージのレポート
  * params_time : 初期時間、モデルの期間、出力頻度など
  * params_grid : グリッドの種類（曲線、直交など）および配列サイズ
  * params*files : 出力の種類（use*mdsio、use_mnc）および配列サイズ（ioSize）
  * completed : 標準出力ファイル（filout）の終了に応じてtrue / false
