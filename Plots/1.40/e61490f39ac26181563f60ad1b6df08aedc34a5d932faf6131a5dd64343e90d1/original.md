`default(key)` returns the current default value for that key.

`default(key, value)` sets the current default value for that key.

`default(; kw...)` will set the current default value for each key/value pair.

`default(plotattributes, key)` returns the key from plotattributes if it exists, otherwise `default(key)`.
