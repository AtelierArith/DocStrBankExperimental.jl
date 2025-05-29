```
isinferred(output::Output, ruleset::Ruleset)
isinferred(output::Output, rules::Rule...)
```

Test if a custom rule is inferred and the return type is correct when `applyrule` or `applyrule!` is run.

Type-stability can give orders of magnitude improvements in performance.
