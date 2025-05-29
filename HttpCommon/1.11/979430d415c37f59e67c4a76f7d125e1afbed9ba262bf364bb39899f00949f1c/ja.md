```markdown
parsequerystring(query::String)

有効なクエリ文字列を Dict に変換します:

```

q = "foo=bar&baz=%3Ca%20href%3D%27http%3A%2F%2Fwww.hackershool.com%27%3Ehello%20world%21%3C%2Fa%3E" parsequerystring(q)

# Dict{String,String} で 2 エントリ:

# "baz" => "<a href='http://www.hackershool.com'>hello world!</a>"

# "foo" => "bar"

```
