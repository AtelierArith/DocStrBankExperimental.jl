```
@m_str -> String
```

スタイルとチョンプインジケーターに従ってマルチライン文字列リテラルを操作します（終了引用の後に提供されます）：

  * スタイルインジケーター：

      * `f` 改行をスペースに置き換えます（折りたたみ、デフォルト）
      * `l` 改行を保持します（リテラル）
  * チョンプインジケーター：

      * `s` 終わりに改行なし（ストリップ、デフォルト）
      * `c` 終わりに単一の改行（クリップ）
      * `k` 終わりからすべての改行を保持します（キープ）

スタイルとチョンプインジケーターの両方が提供されている場合、スタイルインジケーターは最初に指定する必要があります。

文字列補間は依然として尊重され、補間から追加された改行も処理されます。

詳細については[https://yaml-multiline.info](https://yaml-multiline.info)を参照してください。

# 例

```jldoctest; setup = :(using MultilineStrings)
julia> m"""
       A string written
       over multiple lines
       """
"A string written over multiple lines"
```
