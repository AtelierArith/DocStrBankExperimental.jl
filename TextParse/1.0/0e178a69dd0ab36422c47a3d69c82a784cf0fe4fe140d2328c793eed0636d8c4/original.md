`Quoted(inner::AbstractToken; <kwargs>...)`

# Arguments:

  * `inner`: The token inside quotes to parse
  * `required`: are quotes required for parsing to succeed? defaults to `false`
  * `includequotes`: include the quotes in the output. Defaults to `false`
  * `includenewlines`: include newlines that appear within quotes. Defaults to `true`
  * `quotechar`: character to use to quote (default decided by `LocalOpts`)
  * `escapechar`: character that escapes the quote char (default set by `LocalOpts`)
