Match expression `ex` to a pattern `pat`, return nullable dictionary of matched symbols or rpatpressions. Example:

```
ex = :(u ^ v)
pat = :(_x ^ _n)
matchex(pat, ex)
# ==> Union{ Dict{Symbol,Any}(:_n=>:v,:_x=>:u), Void }
```

NOTE: two symbols match if they are equal or symbol in pattern is a placeholder. Placeholder is any symbol that starts with '*'. It's also possible to pass list of placeholder names (not necessarily starting wiht '*') via `phs` parameter:

```
ex = :(u ^ v)
pat = :(x ^ n)
matchex(pat, ex; phs=Set([:x, :n]))
# ==> Union{ Dict{Symbol,Any}(:n=>:v,:x=>:u), Void } 
```

Several elements may be matched using `...` expression, e.g.:

```
ex = :(A[i, j, k])
pat = :(x[I...])
matchex(pat, ex; phs=Set([:x, :I]))
# ==> Union{ Dict(:x=>:A, :I=>[:i,:j,:k]), Void }
```

Optional parameters:

  * phs::Set{Symbol} = DEFAULT_PHS[1]     A set of placeholder symbols
  * allow_ex::Boolean = true     Allow matchinng of symbol pattern to an expression. Example:

    ```
        matchex(:(_x + 1), :(a*b + 1); allow_ex=true)  # ==> matches
        matchex(:(_x + 1), :(a*b + 1); allow_ex=false)  # ==> doesn't match
    ```
  * exact::Boolean = false     Allow matching of the same expression to different keys

    ```
        matchex(:(_x + _y), :(a + a); exact=false) # ==> matches
        matchex(:(_x = _y), :(a + a); exact=true)  # ==> doesn't match
    ```
