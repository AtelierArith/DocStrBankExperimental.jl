```
function process_focus(widget, k::Keystroke)
```

Process the actions when widget `widget` is in focus and the keystroke `k` is pressed. If it returns `false`, then it is means that the widget was not capable to process the focus. Otherwise, it must return `true`.
