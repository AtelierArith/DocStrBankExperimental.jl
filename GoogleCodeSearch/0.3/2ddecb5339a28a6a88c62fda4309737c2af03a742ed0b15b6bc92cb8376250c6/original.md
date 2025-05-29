Search by calling the search method with a regex pattern to search for. Optionally pass the following parameters:

  * `ignorecase`: boolean, whether to ignore case during search (default false)
  * `pathfilter`: a regular expression string to restrict search only to matching paths

The search method returns a vector of named tuples, each describing a match.

  * `file`: path that matched
  * `line`: line number therein that matched
  * `text`: text that matched
