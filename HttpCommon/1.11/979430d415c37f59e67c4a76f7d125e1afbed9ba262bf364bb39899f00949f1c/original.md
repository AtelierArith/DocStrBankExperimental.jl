parsequerystring(query::String)

Convert a valid querystring to a Dict:

```
q = "foo=bar&baz=%3Ca%20href%3D%27http%3A%2F%2Fwww.hackershool.com%27%3Ehello%20world%21%3C%2Fa%3E"
parsequerystring(q)
# Dict{String,String} with 2 entries:
#   "baz" => "<a href='http://www.hackershool.com'>hello world!</a>"
#   "foo" => "bar"
```
