Given text and a regular expression that matches a markdown link, extract and return a vector of markdown links from within that text.

## Arguments

  * `text::String` - text to be processed

## Keyword Arguments

  * `key_regex::Regex` - regular expression to capture markdown links; default captures markdown links of the form, `[linked text](https:://duckduckgo.com)`
  * `group_links::Bool` - a boolean that determines if the function should try to determine what kind of link a markdown link is (e.g. a website link, a relative file link, etc.) and returns a dictionary instead of a vector with only the links

## Returns

  * Vector of strings with captured markdown links
