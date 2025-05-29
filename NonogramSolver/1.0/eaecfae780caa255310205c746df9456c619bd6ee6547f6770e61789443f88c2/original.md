```
read_puzzle_from_cwc(cwcFileName::String) -> Puzzle
```

Import a puzzle that was exported from [Web Paint-by-Number](https://webpbn.com/export.cgi) as a .CWC file.

# Example

With `puzzle.cwc` exported from Web Paint-by-Number and placed in the working directory, we may then build:

```julia
puzzle = read_puzzle_from_cwc("puzzle.cwc")
```
