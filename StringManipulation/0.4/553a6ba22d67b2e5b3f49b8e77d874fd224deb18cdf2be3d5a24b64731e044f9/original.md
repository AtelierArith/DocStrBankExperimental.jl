```
split_string(str::AbstractString, size::Int) -> String, String
```

Split the string `str` after a number of characters that have a specific printable `size`. This function returns two strings: before and after the split point.

The algorithm ensures that the printable width of the first returned string will always be equal `size`, unless `size` is negative or larger than the printable size of `str`. In the first case, the first string is empty, whereas, in the second case, the first string is equal to `str`.

!!! note
    If the character in the split point needs more than 1 character to be printed (like some UTF-8 characters), everything will be filled with spaces.

