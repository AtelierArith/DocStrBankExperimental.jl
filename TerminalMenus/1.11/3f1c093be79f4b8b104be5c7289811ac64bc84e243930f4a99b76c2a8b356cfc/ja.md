```
MultiSelectMenu
```

ユーザーがリストから複数のオプションを選択できるメニューです。

# サンプル出力

```julia
julia> request(MultiSelectMenu(options))
好きな果物を選んでください:
[press: d=done, a=all, n=none, <enter>=select]
   [ ] りんご
 > [X] オレンジ
   [X] ブドウ
   [ ] イチゴ
   [ ] ブルーベリー
   [X] モモ
   [ ] レモン
   [ ] ライム
あなたが好きな果物:
  - オレンジ
  - ブドウ
  - モモ
```
