```
strout = localstring(title, checkfun=s->true)
```

Get a user specific string, and ask the user if they haven't given it before. checkfun(string) is run, and only returns the string if true.
