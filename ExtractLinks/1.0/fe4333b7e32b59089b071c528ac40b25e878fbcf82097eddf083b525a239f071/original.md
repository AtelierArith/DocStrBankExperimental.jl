```
extract_links(url::AbstractString; body::AbstractString=String(HTML.get(url).body))
```

Extract a list of links on webpage hosted at `url`.

Automatically resolves relative links relative to `url`.

The `body` of the page will be automatically downloaded if not provided.

`url` must be an absolute URL starting with http:// or https://.

The links are returned as a vector of unique strings in arbitrary order.

Makes a best effort to extract links from malformed HTML and should not throw due to malformed HTML.

Due to the finniky nature of the web, this can only make a best effort, even if the HTML is well-formed. The exact huristics used are subject to change in a non-breaking release.
