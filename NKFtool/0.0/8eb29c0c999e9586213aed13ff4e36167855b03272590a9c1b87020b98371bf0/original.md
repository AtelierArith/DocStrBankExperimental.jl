```
nkf_guess(from::IO)
```

Try to guess the encoding of the input stream `from`, and return a string representing its encoding.

# Examples

```julia-repl
julia> nkf_guess(IOBuffer(raw"こんにちわ"))
"UTF-8"

julia> open("hello_sjis.txt","w") do f
           print(f, nkf_convert(raw"こんにちわ", "-s"))
       end
       #
       encoding=open("hello_sjis.txt") do f
           nkf_guess(f)
       end
"Shift_JIS"
```
