```
TreeMenu(root; pagesize::Int=10, dynamic = false, maxsize = pagesize, keypress = (m,i) -> false, kwargs...)
```

Use `root` to create an interactive menu using TerminalMenus. `pagesize` is the number of lines to use for a page. If `dynamic`, adjust the page size based on the expansion of the content. `maxsize` is the maximum size of the page.

Provide a function `keypress` to respond to keys while the menu is shown. The function has two arguments, `m::TreeMenu` and `i::UInt32`. The integer `i` is the key pressed. This function should return `true` if the menu should exit and `false` otherwise.

`kwargs` are passed to `TerminalMenus.Config`.
