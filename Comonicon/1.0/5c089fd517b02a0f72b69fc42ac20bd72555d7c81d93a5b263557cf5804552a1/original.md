```
cmd_exit(code::Int = 0)
```

Exit the CLI program with `code`. This method is preferred over `exit` to make sure the program won't exit directly without handling the exception.
