```
FString(L, s::String)
```

Convert the Julia `String` `s` to an `FString{L}`. `s` must contain only ASCII characters. As in Fortran, the string will be padded with spaces or truncated in order to reach the desired length.
