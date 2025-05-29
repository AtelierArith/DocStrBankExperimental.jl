```
get_citations(; only_direct=false, filename="julia_citations.bib")
```

This function will create a .bib file with all the citations collected form the CITATION.bib files corresponding to the dependecies of the current active environment. Use `filename` to change the name of the file. To include just the direct dependencies use `only_direct=true`. Use `badge = true` to get the citations from packages without a `Citation.bib` file, but with a DOI badge.
