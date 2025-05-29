```
locale_id([gloc::Locale, ]category)
```

Determine current locale id for given category as stored in locale variable. If gloc is not given, use task specific locale variable. Throw exception, if no valid category name. Valid categories are :CTYPE, :COLLATE, :MESSAGES, :MONETARY, :NUMERIC, :TIME
