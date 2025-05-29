```
qstart(;debug = false, qwtw_test = false, libraryName = "libqwtw", marblePluginPath = "")::Int32
```

はqwtw "C" ライブラリを開始します。これがないと、何も機能しません。他の関数の前に呼び出してください。

  * debugの場合、デバッグ出力を有効にしようとします。多くの情報が出力されます。デバッグ用です。
  * qwtw_test -> trueの場合、環境変数を変更しないようにしようとします。
  * libraryName: 空でない場合、アーティファクトからのライブラリの代わりにこれをライブラリ名として使用します（デバッグ用）。
  * marblePluginPath: 'Marbleプラグイン'の代替場所。独自のMarbleライブラリのビルドがある場合に使用します（地図を描画するために使用）。

成功した場合は0を返します。
