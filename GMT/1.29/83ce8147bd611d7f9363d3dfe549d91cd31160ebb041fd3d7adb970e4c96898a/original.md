```
bissextile(year::Integer) -> Bool
```

Extremly fast function to check if a year is bissextile (leap year). See https://hueffner.de/falk/blog/a-leap-year-check-in-three-instructions.html

It falls back to classic method for years < 0.
