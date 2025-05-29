```
tldr(str, print=true)
```

The main function of `tldr`, called when the `tldr>` REPL or `tldr"str"` are used. The passed `str` determines what kind of search is made.

  * `str` is either `?` or `help`: equivalent to `tldr> pkg:tldr`.
  * `str = pkg:something`: searches for commands associated to the package `something`.
  * `str = cmd:something`: searches for commands matching `something`.
  * `str = something`: Equivalent to `cmd:something`.
