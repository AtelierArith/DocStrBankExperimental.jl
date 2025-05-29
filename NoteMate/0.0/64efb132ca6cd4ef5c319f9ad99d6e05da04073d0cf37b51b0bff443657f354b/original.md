```
generate_franklin_template()
```

Generates a template for a Franklin markdown page.

# Keyword Arguments

  * `title`: Page title. Default is `nothing`
  * `slug`: Specifies web page url path (after base path). Default is `nothing`
  * `tags`: Keywords or tags associated with page. Default is `nothing`
  * `description`: Description of page contents. Default is `nothing`
  * `rss_title`: Page title that shows up on RSS feeds. Default is `nothing`
  * `rss_description`: Description that goes along with RSS updates. Default is `nothing`
  * `rss_pubdate`: Publication date for RSS feed. Default is `nothing`

These kwargs are "page variables" that come directly from `Franklin.jl`'s documentation. For more specific details, please see [Page Variables](https://franklinjl.org/syntax/page-variables/) 

# Return

  * A `String` object that contains a valid Franklin template that can then be modified further

# Example

If the following call is made: `generate_franklin_template(; title = "All-Payer Claims Database", tags = ["apcd", "claims", "database"])`, the following string will be returned:

```
+++

title = "All-Payer Claims Database"

tags = ["zettel", "apcd", "claims", "database", "archive"]

+++

```

This can then be edited or formatted further as needed.
