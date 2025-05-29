```
occurrence_download([key::String]; [filename])
```

`occurrence_request`によって返された発生キーのデータをダウンロードします。引数なしで呼び出すと、`occurrence_request`の最後の結果をダウンロードします。

`occurrence_download`は、gbif.orgがダウンロードを準備することに依存しています。それ以前に呼び出すと、ページが見つからないため404エラーが発生します。

`filename`キーワードを使用して、結果のファイルに名前を付けることができます。

# 例

標高100m未満の一般的なマイナー鳥をすべてリクエストします：

```
sp = species_match("Acridotheres tristis");
token = occurrence_request(sp, username="my_gbif_username", elevation=<(100))
write("mydownloadtoken", string(token)) # 念のため保存します
# ダウンロードの準備ができるまで待ちます
# 必要に応じて、トークンを再度読み取ります：
token = readlines("mydownloadtoken")[1]
# そしてダウンロードします
filename = GBIF2.occurrence_download(token)
```
