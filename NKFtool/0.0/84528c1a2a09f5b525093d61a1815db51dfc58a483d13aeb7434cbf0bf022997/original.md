```
nkf_convert(from::String, options="-w -m0")
```

Convert the input string `from` to the encoding specified by the option directive `options`, and return the output text string, which is just the result of the command line `echo <from> | nkf <options>`.

# Arguments

  * `from::String`: the input string
  * `options::String`: the option directive to be passed to nkf command.

      * Output encoding

          * `-j` : ISO-2022-JP
          * `-s` : Shift_JIS
          * `-e` : EUC-JP
          * `-w[8[0],{16,32}[{B,L}[0]]]` : UTF with options
      * Input encoding

          * `-J` : ISO-2022-JP
          * `-S` : Shift_JIS
          * `-E` : EUC-JP
          * `-W[8,[16,32][B,L]]` : UTF with option
      * MIME decode : `-m[BQSN0]`

          * B:base64
          * Q:quoted
          * S:strict
          * N:nonstrict
          * 0:no decode
      * MIME encode : `-M[BQ]`

          * B:base64
          * Q:quoted

# Examples

```julia-repl
julia> nkf_convert(raw"こんにちわ", "-w -m0")
"こんにちわ"

julia> using Base64

julia> nkf_convert( raw"こんにちわ", "-j") |> base64encode
"GyRCJDMkcyRLJEEkbxsoQg=="

julia> String(base64decode(ans)) |> nkf_convert
"こんにちわ"
```
