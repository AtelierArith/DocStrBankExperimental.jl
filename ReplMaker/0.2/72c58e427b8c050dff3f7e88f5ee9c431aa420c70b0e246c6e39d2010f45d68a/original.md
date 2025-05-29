an extension of `REPL.LineEdit.transition` to achieve handy use.

When

  * giving 3 arguments(action, mistate, mode), it equals to `REPL.LineEdit.transition`.
  * giving 2 arguments(mistate, mode), there is a default 'action' copying the current buffer to the target REPL mode.
  * giving 1 argument(mode), the action is the same as the case of 2 arguments, and 'mistate' is default to be `Base.active_repl.mistate`
