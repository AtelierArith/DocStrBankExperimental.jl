```
append_keymaps!(keymaps, repl::HeaderREPL{H})
```

Append `Dict{Any,Any}` key maps to `keymaps` in order of highest priority first. Some typically useful keymaps (in conventional order of priority):

  * [`trigger_search_keymap`](@ref)
  * [`mode_termination_keymap`](@ref)
  * [`trigger_prefix_keymap`](@ref)
  * `REPL.LineEdit.history_keymap`
  * `REPL.LineEdit.default_keymap`
  * `REPL.LineEdit.escape_defaults`
