`EventSeries` は `values` のベクターとそれに対応する `timestamps` を保持します。`EventSeries` は `AbstractVector` のサブタイプであり、`timestamps` と `values` の両方は `AbstractVector` のサブタイプでなければなりません。

EventSeries(timestamps::U, values::W, ::TrustInput)

```
- `timestamps` と `values` が等しい長さであり、`timestamps` がソートされていることを前提とします。
```

EventSeries(timestamps, values; drop*repeated=true, keep*end=true)

```
- `timestamps` と `values` が等しい長さであることを確認します
- `timestamps` がソートされていることを確認します
- 上記のチェックのいずれかが失敗した場合、`AssertionError` をスローします。
- `drop_repeated` が true (デフォルト) の場合、values 内のすべての重複した値とそれに対応するタイムスタンプは、構築前に削除されます。
- `keep_end` が true (デフォルト) の場合、values の最後の値 (それに対応するタイムスタンプと共に) は、前の値と等しいかどうかに関わらず保持されます。keep_end は `drop_repeated` が true の場合のみ考慮されます。
```
