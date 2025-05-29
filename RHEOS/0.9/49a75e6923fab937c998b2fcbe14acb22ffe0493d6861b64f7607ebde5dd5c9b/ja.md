```
importcsv(filepath::String; delimiter=',', header=false, comment = "CSVファイルからインポート", savelog = true, kwargs...)
```

CSVファイルからデータを読み込みます（デフォルトではカンマ区切りの2列または3列ですが、`delimiter`キーワード引数で区切り文字を指定できます）。

この関数は、提供されたパラメータや列名に応じて、`RheoTimeData`インスタンスまたは`RheoFreqData`インスタンスを構築するために使用できます。関数は、時間または周波数が含まれているかを検出し、それに応じて処理を進めます。振動データの場合、すべての3列（Gp、Gpp、周波数）を提供する必要があります。通常の粘弾性データの場合は、時間、または時間-応力、または時間-ひずみ、または時間-応力-ひずみデータのみを提供できます。

列は、値またはヘッダー名（大文字と小文字を区別しない）をキーワードパラメータとして提供することで、CSVファイル内で指定できます。

`importcsv("filename.csv", time=1, strain=2, stress=3)`は、最初の列に時間、2番目の列にひずみ、3番目の列に応力があるCSVファイルから`RheoTimeData`を読み込みます。

`importcsv("filename.csv", omega="Frequency", Gp="Storage", Gpp="Loss")`は、CSVファイルのヘッダーを読み取ることで列番号を検出します。

情報が提供されない場合、関数は標準名を期待してヘッダー名から列を検出しようとします。認識されるキーワードの一部は、`time`、`stress`、`strain`、`frequency`、`storage modulus`、`loss modulus`です。

CSVファイルにヘッダーが含まれている場合でも、ヘッダー文字列ではなく列番号で列を示すことを好む場合は、キーワード`header`を`true`に設定する必要があります。
