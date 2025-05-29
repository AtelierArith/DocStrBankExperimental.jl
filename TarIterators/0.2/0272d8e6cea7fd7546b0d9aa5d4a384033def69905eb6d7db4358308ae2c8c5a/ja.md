```
TarIterator(io[, predicate])
```

読み取り用に開かれた入力ストリーム上のイテレータ。`io` は既存の tar ファイルのパス名であることもできます。ストリームまたはファイル内のデータは、パッケージ `Tar` が理解する `tar` ファイル形式に従う必要があります。

`predicate` が指定されている場合、一致するヘッダーデータを持つ tar 要素のみが処理されます。

  * `String` または `Regex`: `predicate` は要素名に適用されます。
  * `Symbol`: `Tar.Header` のフィールド `type` と一致する必要があります。
  * ブール関数: 要素の `Tar.Header` に適用されます。
  * `Tuple`: タプル内のすべての述語の AND
  * `Vector`: ベクター内のすべての述語の OR

例:

```
    io = open("/tmp/abc.tar") 
    TarIterator(io)              # すべてのエントリ 
    TarIterator(io, :file)       # ファイルタイプのすべてのエントリ 
    TarIterator(io, "y")         # 名前が "y" のエントリのみ 
    TarIterator(io, r".*[.]txt") # 名前が ".txt" で終わるすべてのエントリ
    TarIterator(io, h -> h.size > 100) # データサイズが 100 を超えるエントリのみ
```
