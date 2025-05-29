EndOfPath represents an error that occured during access to a JSON path. EndOfPath is not an exception. It's just an enum with a few values which may be useful for further processing.

# Fields

  * `MISSING_KEY` - The requested key of an object is missing.
  * `OUT_OF_BOUNDS` - The requested index of a list is out of bounds.
  * `NOT_A_CONTAINER` - Requested access to an object which is not an object or a list.
  * `INVALID_KEY_TYPE` - Requested access to an object using index or to a list using a key.
  * `INVALID_ROOT` - The root object is not a Dict or a Vector. The errors that occure in the root object are separated because the `setindex!` function isn't able to modify the root object so the user might want to handle them in a different way.
