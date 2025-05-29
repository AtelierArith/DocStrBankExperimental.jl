```
JSONText(s::AbstractString)
```

`JSONText` is a wrapper around a Julia string representing JSON-formatted text, which is inserted *as-is* in the JSON output of `JSON.print` and `JSON.json` for compact output, and is otherwise re-parsed for pretty-printed output.

`s` *must* contain valid JSON text.  Otherwise compact output will contain the malformed `s` and other serialization output will throw a parsing exception.
