キー入力によって生成されたイベントに関する詳細。

```julia
struct KeyEvent
```

  * `key_name::Symbol`: 物理キーの名前。
  * `key::WindowAbstractions.KeySymbol`: キーストロークに関連付けられたシンボル。
  * `input::Char`: 印刷可能な入力（空文字列である可能性があります）。
  * `modifiers::WindowAbstractions.ModifierState`: 修飾子の状態。
  * `consumed_modifiers::WindowAbstractions.ModifierState`: 物理キーをキーシンボルに変換する際に使用された修飾子。
