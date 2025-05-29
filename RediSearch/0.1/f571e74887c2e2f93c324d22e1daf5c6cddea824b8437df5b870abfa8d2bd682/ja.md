```
create_index(
    fields;
    client=get_search_client(),
    no_term_offsets=false,
    no_field_flags=false,
    stopwords=nothing,
    definition=nothing,
    max_text_fields=false,
    temporary=nothing,
    no_highlight=false,
    no_term_frequencies=false,
    skip_initial_scan=false,
)
create_index(field::AbstractField; kwargs...) = create_index([field]; kwargs...)
```

指定された仕様でインデックスを作成します。インデックスがすでに存在する場合、エラーが発生します。

# 引数

  * `fields`: フィールドオブジェクトのリスト

# キーワード

  * `client`: 検索クライアント
  * `no_term_offsets`: オフセット用のブール値。
  * `no_field_flags`: フィールドフラグ用のブール値
  * `stopwords`: ストップワードのリスト。何も指定しない場合、デフォルトのストップワードが使用されます。
  * `definition`: インデックス定義オブジェクト。
  * `max_text_fields`: RediSearchに32以上のテキスト属性があるかのようにインデックスをエンコードさせます。
  * `temporary`: 指定された非活動期間後に期限切れになる軽量の一時インデックスを作成します。
  * `no_highlight`: ハイライトサポートを無効にすることで、ストレージスペースとメモリを節約します。
  * `no_term_frequencies`: trueの場合、インデックスに用語頻度を保存しないようにします。
  * `skip_initial_scan`: trueの場合、スキャンとインデックス作成を行いません。
