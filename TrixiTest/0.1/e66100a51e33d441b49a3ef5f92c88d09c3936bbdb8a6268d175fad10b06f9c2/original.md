```
@trixi_test_nowarn expr [additional_ignore_content]
```

Modified version of `@test_nowarn expr` that prints the content of `stderr` when it is not empty and ignores some common info statements. Additional patterns that should be ignored can be passed as a list of strings or regular expressions.
