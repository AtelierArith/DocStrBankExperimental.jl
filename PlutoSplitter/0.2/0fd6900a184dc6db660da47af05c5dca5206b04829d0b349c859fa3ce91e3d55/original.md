Split a notebook file.

  * `notebookfile`: File to split.
  * `type`: Type of splitting to perform.       Can be "check" to only perform some sanity checks, "statement" or "solution".

Keyword arguments:

  * `output_filename`, Optional: The filename to save the processed notebook at, by default `type` is appended to the original filename. `output_filename` can also be a function with two arguments, which will be passed `notebookfile` and `type` and should return the new filename as a String.
