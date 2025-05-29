```
@htl_str -> Result
```

Create a `Result` object with string interpolation (`$`) that uses context-sensitive hypertext escaping. Unlike the `@htl` macro, this string literal does not include escaping feature [1]. To include `$` within user content one must write `&#36;`. Observe that `&quot;` and any other HTML ampersand escape sequence can be used as appropriate.

In this syntax, interpolation is extended beyond regular Julia strings to handle three additional cases: tuples, named tuples (for attributes), and generators. See Julia #38734 for the feature request so that this could also work within the `@htl` macro syntax.

[1] There are also a few edge cases, see `@raw_str` documentation and Julia #22926 for more detail.
