The `VersionParsing` package implements flexible parsing of version-number strings into Julia's built-in `VersionNumber` type, via the `vparse(string)` function.

Unlike the `VersionNumber(string)` constructor, `vparse(string)` can handle version-number strings in a much wider range of formats without throwing an exception.
