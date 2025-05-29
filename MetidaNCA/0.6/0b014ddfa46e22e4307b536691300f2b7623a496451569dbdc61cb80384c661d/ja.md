```
applylimitrule!(data::Union{PKSubject, PDSubject}, rule::LimitRule)
```

PK対象にルールを適用します。

  * ステップ 1 (NaN ステップ): すべての `NaN` および `missing` 値を nan キーワード値で置き換えます (もし `nan` が NaN でない場合)。
  * ステップ 2 (LLOQ ステップ): `lloq` 未満の値を `btmax` 値で置き換えます。この値が Tmax の前であれば、またはこの値が Tmax の後であれば `atmax` で置き換えます (もし `lloq` が NaN でない場合)。
  * ステップ 3 (NaN の削除): `rm` が true の場合、すべての `NaN` および `missing` 値を削除します。
