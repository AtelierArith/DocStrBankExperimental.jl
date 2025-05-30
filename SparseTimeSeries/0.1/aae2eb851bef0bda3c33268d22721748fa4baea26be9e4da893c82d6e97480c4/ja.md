`EventSeries`は、対応する`timestamps`と共に`values`のベクターを保持します。`EventSeries`は`AbstractVector`のサブタイプであり、`timestamps`と`values`の両方は`AbstractVector`のサブタイプでなければなりません。

EventSeries(timestamps::U, values::W, ::TrustInput)

```
- `timestamps`と`values`が等しい長さであり、`timestamps`がソートされていることを前提としています。
```

EventSeries(timestamps, values; drop*repeated=true, keep*end=true)

```
- `timestamps`と`values`が等しい長さであることを確認します
- `timestamps`がソートされていることを確認します
- 上記のチェックのいずれかが失敗した場合、`AssertionError`をスローします。
- `drop_repeated`がtrue（デフォルト）である場合、`values`内のすべての重複した値と対応する`timestamps`は、構築前に削除されます。
- `keep_end`がtrue（デフォルト）である場合、`values`内の最後の値（およびその対応する`timestamp`）は、前の値と等しいかどうかに関係なく保持されます。`keep_end`は、`drop_repeated`がtrueの場合にのみ考慮されます。
```
