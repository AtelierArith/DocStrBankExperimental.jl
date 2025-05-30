日付入力（`<input type="date">`） - ユーザーは日付を選択でき、日付は`@bind`を介して`Dates.DateTime`として返されます。

`default`を使用して初期値を設定します。

`<input type="date">`に関する[Mozillaのドキュメント](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input/date)を参照してください。

# 例

`@bind best_day_of_my_live DateField()`

`@bind best_day_of_my_live DateField(default=today())`
