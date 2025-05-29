```
highlight!(
    q::AbstractQuery; fields::AbstractArray=nothing, tags::AbstractArray=nothing
)

ハイライトは、見つかった用語（およびそのバリエーション）をユーザー定義のタグでハイライトします。
これは、マークアップ言語を使用して一致したテキストを異なる書体で表示したり、テキストを異なる方法で表示したりするために使用できます。
```

# 引数

  * `q::AbstractQuery`: クエリオブジェクト。

# キーワード

  * `fields::AbstractArray`: フィールドのリスト
  * `tags::AbstractArray`: ユーザータグオブジェクト。
