```
runTMS(::SimData)
runTMS(::SimData; clean = true)
runTMS(::SimData; restart = true)
runTMS(::SimData; output = myoutput)
```

与えられたシミュレーションを実行し（詳細はSimDataを参照）、出力をファイルに書き込み、結果を含むSimulationオブジェクトを返します。`clean`（デフォルトは`false`）はシミュレーションディレクトリを削除して終了し、`restart`（デフォルトは`false`）はシミュレーションディレクトリを削除してシミュレーションを実行します。`output`はすべての出力を指定されたIOチャネルにリダイレクトします（出力ディレクトリは作成されません）。便利な値はstdoutまたはdevnull（すべての出力を抑制するため）です。`save_json`（デフォルトは`true`）は、対応するファイルにJSON形式で辞書に蓄積されたデータを保存します。
