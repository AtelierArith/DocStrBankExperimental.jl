```
append_keymaps!(keymaps, repl::HeaderREPL{H})
```

`Dict{Any,Any}` キー マップを最優先の順序で `keymaps` に追加します。一般的に便利なキー マップ (優先順位の通常の順序):

  * [`trigger_search_keymap`](@ref)
  * [`mode_termination_keymap`](@ref)
  * [`trigger_prefix_keymap`](@ref)
  * `REPL.LineEdit.history_keymap`
  * `REPL.LineEdit.default_keymap`
  * `REPL.LineEdit.escape_defaults`
