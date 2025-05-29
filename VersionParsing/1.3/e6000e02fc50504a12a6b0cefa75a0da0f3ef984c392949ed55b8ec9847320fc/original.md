```
vparse(s::AbstractString)
```

Returns a `VersionNumber` representing as much as possible of the version information in the string `s`.  A much wider range of formats is supported than the semver styles recognized by `VersionNumber(s)`.

For example,

  * Non-numeric prefixes are stripped along with any invalid version characters. Commas are treated as decimal points.
  * Text following whitespace after the version number is ignored.
  * `major.minor.patch.x.y.z` is supported, with `x.y.z` prepended to the semver build identifier, i.e. it is parsed like `major.minor.patch+x.y.z`.
  * Multiple `+x+y` build identifiers are concatenated as if they were `+x.y`.
  * A leading `0` is prepended if needed, e.g. `.x` is treated as `0.x`.
  * When all else fails, everything except the first `major.minor.patch` digits found are ignored.
