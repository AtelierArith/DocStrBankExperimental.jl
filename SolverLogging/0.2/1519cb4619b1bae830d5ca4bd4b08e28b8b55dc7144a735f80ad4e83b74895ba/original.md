```
printheader(logger)
```

Prints the header row(s) for the logger, including only the entries that are active at the current verbosity level. The style of the header can be changed via  `logger.opts.headerstyle`, which is a Crayon that applies to the entire header. The repeated character under the header can be specified via `logger.opts.linechar`. This value can be set to the null character ` ` if this line should be excluded.
