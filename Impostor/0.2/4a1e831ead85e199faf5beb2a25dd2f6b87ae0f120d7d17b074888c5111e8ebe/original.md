```
(impostor::ImpostorTemplate)(n::Integer = 1, sink = Dict; kwargs...)
```

Generate `n` entries according to the `format` provided when `impostor` was instantiated.

# Parameters

  * `n`: number of entries/rows to generate in each format
  * `sink = Dict`: type sink for the generated table.

# Kwargs

  * `locale::Vector{String}`: locale(s) from which entries are sampled. If no `locale` is provided, the current session locale is used.

# Examples

```@repl
julia> formats = ["complete_name", "credit_card_number", "credit_card_expiry"];

julia> template = ImpostorTemplate(formats)
ImpostorTemplate([:complete_name, :credit_card_number, :credit_card_expiry])

julia> template(3, DataFrame)
3×3 DataFrame
 Row │ complete_name                  credit_card_number  credit_card_expiry
     │ String                         String              String
─────┼───────────────────────────────────────────────────────────────────────
   1 │ Sophie Cornell Collins         52583708162384822   6/2008
   2 │ Mary Collins Cornell           3442876938992966    10/2022
   3 │ John Sheffard Cornell Collins  4678055537702596    10/2021

julia> template(3, DataFrame; locale = ["pt_BR"])
3×3 DataFrame
 Row │ complete_name                      credit_card_number  credit_card_expiry
     │ String                             String              String
─────┼───────────────────────────────────────────────────────────────────────────
   1 │ João Camargo da Silva Pereira      3418796429393351    4/2018
   2 │ João Pereira da Silva              4305288858368967    6/2018
   3 │ Bernardo Pereira Camargo da Silva  3751513143972989    3/2024
```
