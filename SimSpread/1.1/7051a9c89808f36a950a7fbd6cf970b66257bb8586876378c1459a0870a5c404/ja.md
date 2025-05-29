```
save(filepath::String, fidx::Int64, yhat::NamedMatrix, y::NamedMatrix; delimiter::Char='	')
```

与えられたファイルパスにクロスバリデーション予測をテーブルとして保存します。

# 引数

  * `filepath::String`: 出力ファイルパス
  * `fidx::Int64`: 数値フォールドID
  * `yhat::NamedArray`: 予測されたソース-ターゲット二部隣接行列
  * `y::NamedArray`: グラウンドトゥルースソース-ターゲット二部隣接行列
  * `delimiter::Char`: テーブルを書き込むために使用される区切り文字（デフォルト = '\t'）

# 拡張ヘルプ

テーブル形式は次の通りです：

```
fold, source, target, score, label
```
