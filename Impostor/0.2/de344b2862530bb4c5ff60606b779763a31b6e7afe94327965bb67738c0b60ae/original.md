```
render_template(template locale) :: String
render_template(template, reference_dfrow; locale) :: String
```

Materialize a given pre-defined template by splitting `template` into tokens; each token *may* by associated to a generator-function exported by Impostor. Tokens associated to generator-functions are excpected to have the excact same spelling as their generator-function correspondents (*e.g.* the token "address" is associated to the generator-function `address`).

For practicality, tokens not exported by Impostor (see example below) are just repeated in the materialized template since it is not possible for Impostor to distinguish between badly spelled generator functions and raw text which should be present in materialized template.

Optionally, provide a `reference_dfrow` with column names which may be referenced by tokens in `template`. This is useful in the context of hierarchical data manipulation

# Parameters

  * `template::String`: templaate to be materialized.
  * `reference_dfrow::DataFrames.DataFrameRow`: Reference values stored in a single-row DataFrame (`DataFrameRow`); access to values is made through references to column names of `reference_dfrow` (see examples below).

# Examples

## String Materialization

```@repl
julia> template = "firstname surname occupation";

julia> render_template(template; locale="en_US")
"Charles Fraser Anthropologyst"

julia> template = "I know firstname surname, this person is a(n) occupation";

julia> render_template(template; locale="en_US")
"I know Charles Jameson, this person is a(n) Mathematician"
```

## Missing Tokens

```@repl
julia> template = "firstname lastname"  # not that there is no such 'lastname' function
"firstname lastname"

julia> render_template(template; locale="en_US")
"Kate lastname"
```

## Using `DataFrameRow`s

```@repl
julia> dfrow = DataFrame(state="California", city="San Francisco")[1, :]
1×2 DataFrame
 Row │ state       city
     │ String      String
─────┼───────────────────────────
   1 │ California  San Francisco

julia> template = "I live in city (state)"

julia> render_template(template, dfrow; locale = "en_US")
"I live in San Francisco (California)"
```
