`button(content... = "Press me!"; value=0)`

A button. `content` goes inside the button. Note the button `content` supports a special `clicks` variable, that gets incremented by `1` with each click e.g.: `button("clicked {{clicks}} times")`. The `clicks` variable is initialized at `value=0`. Given a button `b`, `b["is-loading"]` defines whether the button is in a loading state (spinning wheel). Use `b["is-loading"][]=true` or `b["is-loading"][]=false` respectively to display or take away the spinner.
