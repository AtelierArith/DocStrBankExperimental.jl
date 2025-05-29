```
render_alphanumeric(template::AbstractString; numbers, letters) :: String
```

Receive an alphanumeric template string (e.g. `"^^^-####"`) and generate a string replacing:

  * `'#'` chars by random numbers between [0, 9].
  * `'^'` chars by random uppercase letters between A-Z.
  * `'_'` chars by random lowercase letters between a-z.
  * `'='` chars by random uppercase or lowercase letters between a-z|A-Z.

Optionally, provide `numbers` to fill the `'#'` placeholders in `template`; or `letters` to fill `'^'`,`'_'` or `'='` placeholders. Note that if the length of `letters` or `numbers` is smaller than the number of placeholders in each category, the remaining placeholders will be randomly filled according to the character in `template`.

# Examples

```@repl
julia> render_alphanumeric("####")
"6273"

julia> render_alphanumeric("123-####-AAA")
"123-5509-AAA"

julia> render_alphanumeric("__-^^-==-ZZZ123")
"vw-CX-fA-ZZZ123"

julia> render_alphanumeric("__-^^-==-ZZZ###"; numbers = "12345")
"qu-RT-St-ZZZ123"

julia> render_alphanumeric("__-^^-==-ZZZ###"; letters = "AABBCCDD")
"AA-BB-CC-ZZZ427"

julia> render_alphanumeric("__-^^-==-ZZZ###"; letters = "AABBCCDD", numbers = "12345")
"AA-BB-CC-ZZZ123"

julia> render_alphanumeric("_______"; letters = "abc")
"abcomhd"
```
