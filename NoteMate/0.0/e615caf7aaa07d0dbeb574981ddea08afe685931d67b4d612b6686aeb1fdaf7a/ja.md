```
generate_citation()
```

このドキュメントのページを参照するために使用できる引用文字列を生成します。

# 引数

  * `note`: 引用文字列をフォーマットするために使用される `FranklinNote` 構造体

# キーワード引数

  * `citations` : TODO ここでの型と構造を明確にする

# 戻り値

常に `## How to Cite\n\n` で始まる文字列を返し、その後に次のいずれかが続きます：

  * 引用引数が空の場合、主要著者名、ノートタイトル、ホームページリンク、および `monthname day year` 日付を含む標準引用文字列を返します。
  * 引用引数が空でない場合、ノートタイトルの前にすべての著者のリスト、ホームページリンク、および `monthname day year` 日付を含む長い引用文字列を生成します。

FIXME: これは現在、私自身の個人ウェブサイト用にハードコーディングされています。この方法ではないように調整する必要があります。
