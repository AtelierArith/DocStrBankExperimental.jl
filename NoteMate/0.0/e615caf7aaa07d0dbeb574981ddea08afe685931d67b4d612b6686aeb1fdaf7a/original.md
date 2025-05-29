```
generate_citation()
```

Generate the citation string that can be used to reference the page of this document. 

# Arguments

  * `note`: a `FranklinNote` struct whose information will be used to format the citation strings

# Keyword Arguments

  * `citations` : TODO clarify type and structure here

# Return

Return string always begin with `## How to Cite\n\n` followed by either:

  * if the citation argument is empty, returns a standard citation string with primary author name, note title, homepage link and `monthname day year` date.
  * if the citation argument is non-empty, will generate a longer citation string with list of all authors before note title, homepage link and `monthname day year` date.

FIXME: This is currently hardcoded for my own personal website. We need to adjust this to not be that way.
