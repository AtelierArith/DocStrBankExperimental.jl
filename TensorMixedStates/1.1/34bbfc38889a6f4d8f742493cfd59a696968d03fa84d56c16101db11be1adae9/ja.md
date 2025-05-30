```
get_sim_file(::Simulation, filename)
```

指定されたシミュレーションの対応するファイルを返します。"stdout"（または "-"）、"stderr"、および "" はそれぞれ stdout、stderr、および devnull にリダイレクトされ、他の名前はファイル名として解釈されます。

".json" で終わるファイル名は、データを格納するための Dict を返し、このデータは `runTMS` によってファイルに JSON 形式で出力されます。
