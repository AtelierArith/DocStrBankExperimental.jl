```
clean(content::String)
```

Return only the parts of the HTML which are visible in the rendered page. This assumes that a page has changed when a reader can see a change, which seems like a reasonable assumption. Note that this assumption may be violated when a elements are updated on the fly via Javascript.
