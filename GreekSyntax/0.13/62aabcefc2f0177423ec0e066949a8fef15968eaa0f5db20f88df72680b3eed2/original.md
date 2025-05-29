Returns a validated string for `s` from the authority list `authlist`.  A string is considered valid if:

1. its lowercase value appears as a key value in a dictionary of abbreviations
2. its lowercase value is a unique starting value for an item in the authority list
3. its lowercase value matches an item in the authority list within a specified threshhold for Levenshtein edit distance

```julia
validatedform(s, authlist; abbrdict, threshhold)

```
