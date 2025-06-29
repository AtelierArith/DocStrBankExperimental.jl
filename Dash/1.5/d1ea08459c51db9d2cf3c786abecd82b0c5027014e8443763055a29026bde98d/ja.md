```
dcc_interval(;kwargs...)
```

インターバルコンポーネント コンポーネントは、各インクリメントの間に固定の時間遅延を持ってカウンター `n_intervals` を繰り返し増加させます。インターバルは、コンポーネントを定期的にトリガーするのに適しています。時間遅延はミリ秒単位でプロパティ「interval」で設定されます。

  * `id` (String; optional): このコンポーネントのIDで、コールバック内でダッシュコンポーネントを識別するために使用されます。

アプリ内のすべてのコンポーネントで一意である必要があります。

  * `disabled` (Bool; optional): Trueの場合、カウンターはもはや更新されません
  * `interval` (optional): このコンポーネントは、`interval` ミリ秒ごとにカウンター `n_intervals` を増加させます
  * `max_intervals` (optional): インターバルが発火する回数。

-1の場合、インターバルには制限がなく（デフォルト）、0の場合はインターバルが停止します。

  * `n_intervals` (optional): インターバルが経過した回数
