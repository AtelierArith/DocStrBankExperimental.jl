# 関数呼び出し

`save2fig(fileName, subDir="."; dpi=300, tight=true, crop=false)`

# 説明

実際の図を以下の3つのファイル形式で保存します

  * `png` ポータブルネットワークグラフィックス、サブディレクトリ png/ に保存
  * `pdf` エンキャプスulatedポストスクリプト、サブディレクトリ pdf/ に保存

これらの2つのグラフィック形式は、LaTeX、LyX、LibreOffice、または他のワードプロセッサで図を処理する際に関連しています。

# 変数

`fileName` ファイル名の文字列、`.png` および `.pdf` で拡張される; ファイル名はサブディレクトリ `png/` および `pdf/` に保存されます。

`subDir` 隣接するサブディレクトリ `png/` および `pdf/` があるサブディレクトリの文字列; デフォルト = `.` (ローカル作業ディレクトリ)

`dpi` 保存されたPNGファイルの解像度; デフォルト = 300 (dpi)

`tight` 図の周りの追加のマージンが削除され、2%のマージンを除く; デフォルト = `true`

`crop` 図の周りのすべての「白い」スペースをトリミングします; この機能には以下のソフトウェアのインストールが必要です

  * imagemagick を `png` ファイルに適用するため、Windowsでは https://www.imagemagick.org/script/index.php を参照するか、Linux (MintまたはUbuntu) では `sudo apt install imagemagick` を適用します。
  * pdfcrop を `pdf` ファイルに適用するため、Windowsでは https://www.ctan.org/pkg/pdfcrop を参照するか、Linux (MintまたはUbuntu) では `sudo apt install texlive-extra-utils` を適用します。

# 例

```julia
julia> save2fig("phasordiagram")
julia> save2fig("phasordiagram_crop", crop=true)
```
