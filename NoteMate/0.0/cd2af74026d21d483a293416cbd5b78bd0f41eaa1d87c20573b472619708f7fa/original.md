Given text and a regular expression that matches a citation group (e.g. pandoc, etc.), extract and return a vector of citation groups from within that text.

## Arguments

  * `text::String` - text to be processed

## Keyword Arguments

  * `key_regex::Regex` - regular expression to capture citation groups; default captures citation key groups of the form, `[@citation]` or `[@citation_1; @citation_2]`

## Returns

  * Vector of strings with captured citation key groups
