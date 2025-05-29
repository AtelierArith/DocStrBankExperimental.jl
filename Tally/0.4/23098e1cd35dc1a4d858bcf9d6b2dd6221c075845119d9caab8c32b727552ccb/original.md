```
show_style([style::Symbol])
```

With no argument, this function returns the current style used for the `show` method, that is, for printing.

If `style::Symbol` is provided, this sets the show style to `style`. Possible styles are

  * `:table`, the default,
  * `:plot`, print tallies via `Tally.plot`,
  * `:prison`, display the counts using prison mode.
