```
bsindex(old, [ index ]) -> index
```

Save index data (a sorted suffix array) for the content of `old` into `index`. All arguments can be strings or IO handles. If no `index` argument is provided, the index data is saved to a temporary file whose path is returned.

The index can be passed to `bsdiff` to speed up the diff computation by passing `(old, index)` as the first argument instead of just `old`. Since indexing the old data is the slowest part of generating a diff, precomputing this and reusing it can significantly speed up generting diffs from the same old file to multiple different new files.
