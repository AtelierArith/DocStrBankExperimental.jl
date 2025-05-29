```
  item_label(args...; kwargs...)
```

---

### 引数

---

1. 挙動

      * `lines::Union{Int, String}` - 指定された行数で描画するのに十分なスペースがない場合に省略記号を適用します; 例: `1` `3` `lines!="2"`
2. コンテンツ

      * `overline::Bool` - オーバーラインラベルを描画します
      * `caption::Bool` - キャプションラベルを描画します
      * `header::Bool` - ヘッダーラベルを描画します
      * `lines::Union{Int, String}` - 指定された行数で描画するのに十分なスペースがない場合に省略記号を適用します; `1` `3` `lines!="2"`
