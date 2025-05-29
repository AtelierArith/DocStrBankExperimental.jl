```
scrape_tables(url)
scrape_tables(url, cell_transform[=nodeText])
scrape_tables(url, cell_transform[=nodeText], header_transform[=nodeText])
```

This function will scrape `url` for any WELL-FORMED tables wrapped in `<table>` tags and return them in a vector.

# Arguments

```
- `url`: The URL to look for tables
- `cell_transform`: By default, each of the table cells wrapped in `<td>` is transformed by
    the callable (i.e. `Function` or type definition) `cell_transform`. The default
    `cell_transform` is `Cascadia.nodeText` which extracts the node's text. You may wish to use
    `identity` to extract just the cell as a `Gumbo.HTMLNode` type for more advanced processing,
    e.g. `scrape_tables(url, identity)`
- `header_transform`: By default, each of the table header wrapped in `<th>` is transformed by
    the callable (i.e. `Function` or type definition) `header_transform`. The default
    `header_transform` is `Cascadia.nodeText` which extracts the node's text. You may wish to
    use `identity` to extract just the cell as a `Gumbo.HTMLNode` type for more advanced
    processing, e.g. `scrape_tables(url, identity, identity)`
```

# Return

```
`Vector{TableScraper.Table}`
```

The `TableScraper.Table` is a Tables.jl-compatible row-accessible type. So you can convert it to another Tables.jl compatible type if you wish e.g. `DataFrame.(scrape_tables(url))` will return a vector of `DataFrame`s
