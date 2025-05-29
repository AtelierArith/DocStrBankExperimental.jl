```
nkf_guess(from::String)
```

Try to guess the encoding of the input text `from`, and return a string representing its encoding, which is just the result of the command line `echo <from> | nkf -g`.

# Examples

```julia-repl
julia> nkf_guess(raw"こんにちわ")
"UTF-8"

julia> nkf_convert( raw"こんにちわ", "-j") |> nkf_guess
"ISO-2022-JP"

julia> nkf_convert( raw"こんにちわ", "-e") |> nkf_guess
"EUC-JP"

julia> nkf_convert( raw"こんにちわ", "-s") |> nkf_guess
"Shift_JIS"
```
