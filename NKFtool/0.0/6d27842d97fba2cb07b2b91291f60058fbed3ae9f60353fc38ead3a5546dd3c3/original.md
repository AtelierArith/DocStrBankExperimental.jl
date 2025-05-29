```
nkf_convert(from::IO, options="-w -m0")
```

Convert the input stream `from` to the encoding specified by the option directive `options`, and return the output text string, which is just the result of the command line `cat <from> | nkf <options>`

# Arguments

  * `text::String`: the input string
  * `options::String`: the directibr to be passed to nkf command. See [`nkf_convert(from::String, options="-w -m0")`](@ref)

# Examples

```julia-repl
julia> open("hello_sjis.txt","w") do f
           print(f, nkf_convert(raw"こんにちわ", "-s"))
       end
       #
       hello_utf=open("hello_sjis.txt") do f
           nkf_convert(f, "-w -m0")
       end
"こんにちわ"
```
