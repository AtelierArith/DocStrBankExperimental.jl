ローカルファイルのための `Resource` を作成します（base64 エンコードされたデータ URL が生成されます）。

# 警告

`LocalResource` **は機能しません** スクリプト/ノートブックを他の誰かと共有する場合、その人がファイルシステム上でリソースをまったく同じ場所に持っている場合を除いて。

## 推奨される代替手段（画像）

1. [imgur.com](https://imgur.com) にアクセスし、画像をページにドラッグ＆ドロップします。画像を右クリックし、「画像の場所をコピー」を選択します。これで、次のように画像を使用できます: `PlutoUI.Resource("https://i.imgur.com/SAzsMMA.jpg")`。
2. ノートブックが git リポジトリの一部である場合、画像をリポジトリに置き、相対パスを使用します: `PlutoUI.LocalResource("../images/cat.jpg")`。

# 例

```
LocalResource("./cat.jpg")
```

```
LocalResource("/home/fons/Videos/nijmegen.mp4", :width => 200)
```

```
md"""
これはアヒルの鳴き声です: $(LocalResource("../data/hannes.mp3"))
md"""
```
