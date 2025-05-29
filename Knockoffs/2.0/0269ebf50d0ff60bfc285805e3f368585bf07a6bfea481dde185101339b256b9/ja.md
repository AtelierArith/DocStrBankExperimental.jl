```
rapid(rapid_exe, vcffile, mapfile, d, outfolder, w, r, s, [a])
```

RaPIDプログラムのラッパー。

# 入力

  * `rapid_exe`: `RaPID_v.1.7` 実行可能ファイルへのフルパス
  * `vcffile`: フェーズ済みVCFファイル名
  * `mapfile`: マップファイル名
  * `d`: 実際の最小IBD長さ（cM単位）
  * `outfolder`: 出力フォルダ名
  * `w`: サブサンプリングのためのウィンドウ内のSNP数
  * `r`: 実行回数
  * `s`: ヒットと見なすための最小成功数

# オプション入力

  * `a`: `true`の場合、MAFを無視します。デフォルトでは（`a=false`）、サイトはそのMAFに基づいてランダムに選択されます。
