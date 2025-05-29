# 関数呼び出し

`save3fig(fileName, subDir="."; dpi=300, tight=true, crop=false)`

# 説明

実際の図を以下の3つのファイル形式で保存します

  * `png` ポータブルネットワークグラフィックスをサブディレクトリpng/に保存
  * `eps` エンキャプスulatedポストスクリプトをサブディレクトリeps/に保存
  * `pdf` エンキャプスulatedポストスクリプトをサブディレクトリpdf/に保存

これらの3つのグラフィック形式は、LaTeX、LyX、LibreOffice、または他のワードプロセッサで図を処理する際に関連しています

# 変数

`fileName` ファイル名の文字列、`.png`、`.eps`、および`.pdf`で拡張される; ファイル名はサブディレクトリ`png/`、`eps/`、および`pdf/`に保存されます

`subDir` 隣接するサブディレクトリ`png/`、`eps/`、および`pdf/`があるサブディレクトリの文字列; デフォルト = `.`（ローカル作業ディレクトリ）

`dpi` 保存されたPNGファイルの解像度; デフォルト = 300（dpi）

`tight` 図の周りの追加のマージンが削除され、2%のマージンを除く; デフォルト = `true`

`crop` 図の周りのすべての「白い」スペースをトリミング; この機能には以下のソフトウェアのインストールが必要です

  * imagemagickを`png`ファイルに適用するには、Windowsではhttps://www.imagemagick.org/script/index.phpを参照するか、Linux（MintまたはUbuntu）では`sudo apt install imagemagick`を適用します
  * epstoolを`eps`ファイルに適用するには、Windowsではhttp://pages.cs.wisc.edu/~ghost/gsview/epstool.htmを参照するか、Linux（MintまたはUbuntu）では`sudo apt install epstool`を適用します
  * pdfcropを`pdf`ファイルに適用するには、Windowsではhttps://www.ctan.org/pkg/pdfcropを参照するか、Linux（MintまたはUbuntu）では`sudo apt install texlive-extra-utils`を適用します

# 例

```julia
julia> save3fig("phasordiagram")
julia> save3fig("phasordiagram_crop", crop=true)
```
