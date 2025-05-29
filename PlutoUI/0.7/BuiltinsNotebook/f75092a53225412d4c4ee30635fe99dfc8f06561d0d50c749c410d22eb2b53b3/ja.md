Boolean値`true`/`false`を選択するためのチェックボックス。

## 例

`@bind programming_is_fun CheckBox()`

`@bind julia_is_fun CheckBox(default=true)`

`md"そのものが欲しいですか？ $(@bind enable_thing CheckBox())"`
