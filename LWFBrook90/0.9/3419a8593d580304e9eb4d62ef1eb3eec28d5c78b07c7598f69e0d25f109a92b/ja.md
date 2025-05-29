```
prepare_for_LWFBrook90R(s::DiscretizedSPAC; return_value = "inputs", out_dir = ".", file_suffix = "")
```

SPACモデルをRパッケージLWFBrook90Rの入力に変換します。その戻り値は引数return*value ∈ ["results", "inputs", "csv*paths"]に依存します。オプションは次のとおりです：

  * "results":    LWFBrook90Rを実行し、ディスクに書き込まずにJuliaでシミュレーション結果を返します
  * "inputs":     ディスクに書き込まずにJuliaでDataFramesとして入力を返します
  * "csv_paths":  入力を.csvファイルとしてディスクに書き込み、パスを返します ()

Rで実行するための現在の作業ディレクトリ。

`return_value = "results"`の場合、RとLWFBrook90R v0.5.3の作業インストールが必要です。
