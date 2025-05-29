```
ナノ秒日時
```

ナノ秒精度での時間のインスタンスを表す型です。これは、標準の `DateTime` に加えて、`DateTime` が提供するミリ秒解像度に加えたナノ秒の数で構成されています。

# アクセサ関数

  * [`datetime`](@ref): ミリ秒精度での `NanosecondDateTime` の日付と時間を返す `Dates.DateTime` を返します。
  * [`nanoseconds`](@ref): `Date.DateTime` 部分のミリ秒精度を超える追加のナノ秒の数を返す `Dates.Nanosecond` を返します。

# その他の関数

  * [`nearest_datetime`](@ref): `NanosecondDateTime` に最も近い `Dates.DateTime` を返します。

# 拡張された `Dates` 関数

  * `Date`: `NanosecondDateTime` の `Date` 部分を返します。
  * `Time`: フル ns 精度での `NanosecondDateTime` の `Time` 部分を返します。

!!! note
    `NanosecondDateTime` は `DateTime` の全範囲を表すことができますが、ナノ秒精度の miniSEED ファイルは 1677-09-21T00:12:43.145224192 から 2262-04-11T23:47:16.854775807 の範囲内の日付のみを表すことができます。この範囲外の `NanosecondDateTime` を `Int64` に変換しようとすると `InexactError` がスローされます。

