```
fd2text(s; kw)
```

Take a Markdown string and return a version with no markup (used in RSS circumstances). This is bruteforce to say the least, it just discards all HTML tags. It should be safe in that '<' and '>' should have been escaped by the fd2html pass.
