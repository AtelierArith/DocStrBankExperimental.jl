Creates a new FormatSpec by overriding the defaults and passes it to pyfmt

Optionally width and precision can be passed positionally, after the value to be formatted.

Some keyword arguments can be passed simply as symbols:

```
Symbol            | Meaning
------------------|------------------------------------------
:ljust or :left   | Left justified, same as < for FormatSpec
:rjust or :right  | Right justified, same as > for FormatSpec
:center           | Center justified, same as ^ for FormatSpec
:zpad or :zeropad | Pad with 0s on left
:ipre or :prefix  | Whether to prefix 0b, 0o, or 0x
:commas           | Add commas every 3 digits
```

Also, keyword arguments can be given:

```
Keyword | Type | Meaning                   | Default
--------|------|---------------------------|-------
fill    | Char | Fill character            | ' '
align   | Char | Alignment character       | '\0'
sign    | Char | Sign character            | '-'
width   | Int  | Field width               | -1, i.e. ignored
prec    | Int  | Floating Precision        | -1, i.e. ignored
ipre    | Bool | Use 0b, 0o, or 0x prefix? | false
zpad    | Bool | Pad with 0s on left       | false
tsep    | Bool | Use thousands separator?  | false
```
