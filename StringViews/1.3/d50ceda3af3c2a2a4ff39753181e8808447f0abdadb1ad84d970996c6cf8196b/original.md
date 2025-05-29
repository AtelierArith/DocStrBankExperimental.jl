```
SVRegexMatch <: AbstractMatch
```

This type is identical to `RegexMatch` (in Julia `Base`) except that the `match` is a `SubString` of a `StringView` instead of a `String`.

A type representing a single match to a `Regex` found in a string. Typically created from the [`match`](@ref) function.

  * The `match` field stores the substring of the entire matched string.
  * The `captures` field stores the substrings for each capture group, indexed by number. To index by capture group name, the entire match object should be indexed instead, as shown in the examples.
  * The location of the start of the match is stored in the `offset` field.
  * The `offsets` field stores the locations of the start of each capture group, with 0 denoting a group that was not captured.

This type can be used as an iterator over the capture groups of the `Regex`, yielding the substrings captured in each group. Because of this, the captures of a match can be destructured. If a group was not captured, `nothing` will be yielded instead of a substring.
