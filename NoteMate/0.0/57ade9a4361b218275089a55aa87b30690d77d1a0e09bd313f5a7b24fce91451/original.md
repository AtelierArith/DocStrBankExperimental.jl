Given a list of strings denoting a markdown link of the form `[text](link)`, update the link to a relative link format.

## Arguments

  * `link_strings::Vector` - markdown links to be processed

## Keyword Arguments

  * `prefix::String` - a prefix to add to each link; default is `""`

## Returns

  * Dict with keys as the original markdown links and values as their corresponding revised relative links
