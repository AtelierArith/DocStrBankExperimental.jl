```
default{:fieldname}(namedtuple,defval)
```

attempt to get a field `fieldname` from a `NamedTuple`. If `namedtuple` does not have  such a field - or is not a `NamedTuple`, return `defval`.
