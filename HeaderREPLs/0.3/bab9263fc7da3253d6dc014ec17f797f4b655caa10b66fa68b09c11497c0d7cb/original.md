```
keymap_dict = trigger_prefix_keymap(p::PrefixHistoryPrompt)
keymap_dict = trigger_prefix_keymap(repl::HeaderREPL)
```

Sets up the arrow keys and "^P" and "^N" to trigger reverse and forward prefix-search, respectively.
