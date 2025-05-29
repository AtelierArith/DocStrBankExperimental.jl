```
init(always::Bool = false)

GRの環境変数をプロットの前に初期化し、バイナリ共有ライブラリがロードされていることを確認します。初期化は通常1回だけ行う必要がありますが、設定が変更された場合には再初期化が必要になることがあります。

`always`引数は、初期化が現在およびその後の呼び出しで強制されるべき場合にtrueになります。デフォルトでは`false`であり、初期化は1回だけ行われます。

# 拡張ヘルプ

`init`に影響を与える環境変数：
GRDISPLAY - "js"または"pluto"の場合、javascriptサポートが初期化されます
GKS_NO_GUI - 初期化は行われません
GKS_IGNORE_ENCODING - フォントエンコーディングにUTF-8を強制的に使用し、GKS_ENCODINGを無視します

`init`によって設定される環境変数：
GKS_FONTPATH - GRフォントへのパス、通常はGRDIRと同じです
GKS_USE_CAIRO_PNG
GKSwstype - グラフィックスワークステーションのタイプ、`openws`のヘルプを参照してください
GKS_QT - gksqt実行可能ファイルを介してQTバックエンドを起動するためのコマンド
GKS_ENCODING - テキストエンコーディングを設定します（例：Latin1またはUTF-8）
```
