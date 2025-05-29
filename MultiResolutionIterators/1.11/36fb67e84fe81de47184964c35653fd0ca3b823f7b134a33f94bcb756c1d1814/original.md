```
join_levels(iter, lvl_delims::Associative)
```

This is the generalisation of `join`. Use this as `join_levels(doc_sents_words, Dict(1=>" ", 2=" "))`, to join each word with a space, and each sentence  line with a line.

Note that the elements in the level being joined are converted to strings via `string`. This is find if they are already strings, or characters, or numbers etc. But if they are not, e.g. they were nonmerged layers then this often going to be unusual output. But what exactly did you expect it to do? (Answer? Throw an error)
