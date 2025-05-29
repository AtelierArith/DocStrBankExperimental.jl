```julia
write_html_table(io, table; title, caption, options)

```

Write a HTML representation of `table` to `io`.  A file path (string) may be given instead of an `io`.

`title` and `caption` determine respective parts of the table. They will be escaped.

`options` can be used to specify table options, such as CSS.
