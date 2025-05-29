```
         initrepl(parser::Function;
                  prompt_text = "myrepl> ",
                  prompt_color = :blue,
                  start_key = ')',
                  repl = Base.active_repl,
                  mode_name = :mylang,
                  show_function = nothing,
                  show_function_io = stdout,
                  valid_input_checker::Function = (s -> true),
                  keymap::Dict = REPL.LineEdit.default_keymap_dict,
                  completion_provider = REPL.REPLCompletionProvider(),
                  sticky = true,
                  startup_text=true
                  )
```

creates a custom repl mode which takes in code and parses it according to whatever parsing function you provide in the argument `parser`. Choose which key initializes the repl mode with `start_key`, the name of your repl mode with `mode_name` and optionally provide a function which checks if a given repl input is valid before parsing with `valid_input_checker`. Autocompletion options are supplied through the argument `completion_provider` which defaults to the standard julia REPL TAB completions. `prompt_text` may either be a string or a zero-argument function which computes the prompt string.

Aritrary key combinations to enter REPL modes are not yet allowed, but you can currently use the `CTRL` and `ALT`  (also known as `META`) keys as modifiers for entering REPL modes. For example, passing the keyword argument  `start_key="\C-g"` to the `initrepl` function will make it so that holding down on the `CTRL` key and pressing  `g` enters the specified mode.

Likewise, specifying `start_key="\M-u"` will make it so that holding `ALT` (aka `META`) and pressing `u` will enter the desired mode.
