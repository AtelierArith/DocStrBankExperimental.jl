```
generate_note_summary
```

ノートのタイトル、発行日、RSSの要約、および任意のキーワードを使用してノートの要約セクションを生成します。

# 引数

  * `note`: ノートの要約セクション用にフォーマットされた情報を持つ `FranklinNote` 構造体

# 戻り値

  * ノートのタイトルで始まり、`monthname day year` 形式の日付、ノートのRSS要約、およびノートのキーワードをカンマ区切りで続ける、Franklinのオープン知識モデル標準に従ってフォーマットされた文字列。

フォーマットの例:

```
Example title:
=========

**Date:** May 12 2020

**Summary:** This is the summary of an example note

**Keywords:** example files, demonstration, documentation
```
