```
function baseddump

5 methods.
```

function baseddump(io::IO, data::Vector{UInt8}; base = 16, offset = 0, len = -1) function baseddump(io::IO, data; base = 16, offset = 0, len = -1) function baseddump(data; base = 16, offset = 0, len = -1)

```
Print (to stdout, or if specified io) a dump of `data`. The function will attempt
to convert non-UInt8 data to a vector of UInt8 bytes. If a string is passed for 
data, the function will interpret this as a file name for the data, so for string
data textdump() should be used, as shown below. The portion of data that is 
dumped defaults to all of data, or else, if specified, from `offset` to `len`.
The `offset` is printed as the first hex numeric entry on the left, and the final
count of bytes dumped is printed as the last hex number on the left.
The `base` used to print the data is between 16 (default) and 2 (binary).
The data is formatted similar to the format of the unix utilities `hexdump` or
`xxd` for bases 16 and 2, the decimal format for `base` 10 is similar to unix
`hexdump` but with decimal format and similarly for base 8 and octal format.
Any base between 2 and 16 is supported, but there are shorter function names
for base 2 (binary), base 8 (octal), base 10 (decimal), and the default 16
(hexadecimal).
```

function baseddump(to::IO, from::IO; base = 16, offset = 0, len = -1) function baseddump(to::IO, filename::AbstractString; base = 16; offset = 0, len = -1)

```
Print (to stdout, or if specified to the IO `to`) a dump of the stream `from` or file
`filename` as bytes. The portion dumped defaults to all of the data until eof(),
or else, if specified, from `offset` to `len`.
```

Note that these functions have shorter versions `hexdump` which defaults to base 16, `xxd` which defaults to base 2, and `decdump` which defaults to base 10.

Examples:

```
hexdump("test.so") will dump the contents of file "test.so" as a hex display to stdout.

xxd(stderr, s, offset = 16, length = 1008) will dump the bytes in s[16:16+1008-1], where s
is a vector of bytes, to stderr in a binary format.
```
