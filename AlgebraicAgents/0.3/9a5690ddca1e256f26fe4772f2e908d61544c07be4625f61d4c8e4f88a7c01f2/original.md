```
by_name(agent, name::Union{Glob.FilenameMatch, Regex})
```

Return agents in the hierarchy whose names match the given wildcard. If `inners_only==true`, consider descendants of `agent` only.
