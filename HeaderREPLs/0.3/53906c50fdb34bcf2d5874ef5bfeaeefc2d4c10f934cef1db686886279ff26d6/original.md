```
find_prompt(mi, "julia")
find_prompt(mi, PrefixHistoryPrompt)
```

Return the selected prompt from `mi`, searching either for the prompt-string of a `Prompt` or, for other `TextInterface`s, searching by type.
