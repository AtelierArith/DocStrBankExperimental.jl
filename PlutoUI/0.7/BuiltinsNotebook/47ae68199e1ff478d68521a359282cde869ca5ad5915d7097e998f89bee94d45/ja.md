日付入力（`<input type="date">`） - ユーザーは日付を選択でき、日付は`@bind`を介して`Dates.DateTime`として返されます。

`default`を使用して初期値を設定します。

!!! warning "古い情報"
    これは`DateField`ですが、はるかに優れた新しい関数[`DatePicker`](@ref)を使用するべきです！これは`DateTime`の代わりに`Date`を直接返します。


# 例

`@bind best_day_of_my_life DateField()`

`@bind best_day_of_my_life DateField(default=today())`

# 参照

[`DatePicker`](@ref)
