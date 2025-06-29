Define a Parsing Expression Grammar via a macro and abuse of Julia syntax.

  * Rules: `@rule name = expression`
  * Choice: infix `,`
  * Sequence: infix `&`
  * Positive lookahead: prefix `+`
  * Negative lookahead: prefix `-`
  * Option (zero or one time): postfix `[:?]` (≡ `[0:1]`)

      * (note that [?] won't work in Julia >= 1.0 per JuliaLang/julia#22712)
  * Zero or more times: postfix `[*]` (≡ `[0:end]`)
  * One or more times: postfix `[+]` (≡ `[1:end]`)
  * Exactly `m` times: postfix `[m]` (≡ `[m:m]`) (where m is an integer)
  * Between `m` and `n` times inclusive: postfix `[m:n]`
  * At most `n` times: postfix `[0:n]`
  * At least `m` times: postfix `[m:end]`
  * Terminals: `r"regex"`, `"string"`

      * Extra regex flags: `p` is for punctuation, and eats whitespace (`\s*`) after the match; `w` is for word, and implies `p`, but also makes sure match boundaries are word boundaries (`\b`); `h` modifies `p` and `w` to eat only horizontal whitespace (`\h`). Values passed to semantics functions exclude eaten whitespace.
  * Semantics: `expression |> unary_function` (like ParserCombinator)

      * or `expression > nary_function` to interpolate args.
      * Returning the special singleton value `PEG.Failure()` from a semantics function causes the parsing expression it's attached to to fail (return `nothing` instead of a tuple). Returning `nothing` from a semantics function is not special; it just makes the first part of the tuple `nothing`. See the parsing function signature below.

Put another way:

```julia
using PEG
@rule grammar = "using PEG\n" & rule[*]
@rule rule = r"@rule"p & nonterminal & r"="p & choice
@rule choice = seq & (r","p & seq)[*]
@rule seq = item & (r"&"p & item)[*] & (r"\|?>"p & julia_function)[:?]
@rule item = lookahead , counted
@rule lookahead = r"\("p & (r"[+-]"p) & seq & r"\)"p
@rule counted = single & (count)[:?]
@rule count = range , r"\["p & (":?" , r"[\*\+]"p) & r"]"p
@rule range = r"\["p & integer & (r":"p & (integer , r"end"w))[:?] & r"]"p
@rule integer = r"\d+"w
@rule single = parens , terminal , nonterminal
@rule parens = r"\("p & choice & r"\)"p
@rule nonterminal = r"\pL\w+"w
@rule terminal = regex , string & r"\s*"
@rule regex = r"\br" & string & r"[himpswx]*\s*"
@rule string = r""(\\.|[^"])*""
@rule julia_function = # left as an exercise ;)
```

Each rule defines a parsing function with the following signature:

```julia
nonterminal(input::T, cache=PEG.Cache()) where T <: AbstractString
  ::Union{Nothing,Tuple{Any,SubString}}
```

The `Any` part of the return value is the abstract syntax tree, while the `SubString` is the remaining input after the parsed portion. If parsing fails, `nothing` is returned.

While you can use rules defined in this way directly, it might be more convenient to use the functions `parse_next(rule, input; whole=false)` or `parse_whole(rule, input)`. See their documentation for more information.

Call `PEG.setdebug!()` to have debugging information printed during parsing. Call `PEG.setdebug!(false)` to turn it off again.
