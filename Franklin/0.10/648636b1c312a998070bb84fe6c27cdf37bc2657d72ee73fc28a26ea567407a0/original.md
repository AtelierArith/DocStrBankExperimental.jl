```
fd2html(s; kw)
```

Take a Markdown string and return the HTML that Franklin would produce for it.

# Keywords

  * `internal=false`: if set to true, the current scope (in terms of page variables) will                   be passed to process the String, otherwise the string will be processed                   in an isolated scope.
  * `dir=""`: if given and if `internal=false`, sets up a temporary dir for Franklin           processing.
  * `nop=false`: if set to true, check if the returned HTML string has a starting `<p>` and              ending `</p>` and, if so, strips them off. This should be used with care:              for simple strings this is likely to be ok but for strings which would              contain multiple paragraphs (e.g. with headers) this may not work well.
