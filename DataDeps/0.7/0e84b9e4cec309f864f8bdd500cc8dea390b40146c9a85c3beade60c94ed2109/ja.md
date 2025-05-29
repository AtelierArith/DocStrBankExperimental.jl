```
resolve(datadep, inner_filepath, calling_filepath)
```

datadepを含むフォルダーへのパスを返します。依存関係をダウンロードしてそこに置くことを意味する場合でもです。

```
 - `inner_filepath` はデータディレクトリ内のファイルへのパスです
 - `calling_filepath` はこれが呼び出されているファイルへのパスです
```

これは基本的に文字列マクロ `datadep"DepName/inner_filepath"` の背後にある関数です。
