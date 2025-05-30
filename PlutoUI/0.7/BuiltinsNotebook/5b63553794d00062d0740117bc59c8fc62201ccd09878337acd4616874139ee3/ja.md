A time input (`<input type="time">`) - ユーザーは時間を選択でき、時間は `@bind` を介して `String` として返されます（例: `"15:45"`）。値は時間が選択されるまで `""` です。

`default` を使用して初期値を設定します。

[Mozilla の `<input type="time">` に関するドキュメント](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/time)を参照してください。

!!! warning "古い情報"
    これは `TimeField` ですが、私たちの新しい関数 [`TimePicker`](@ref) を使用するべきです。これははるかに優れています！ `String` ではなく、Julia の `Time` を直接返します。


# 例

`@bind lunch_time TimeField()`

`@bind lunch_time TimeField(default=now())`

# 参照

[`TimePicker`](@ref)
