```
aitemplates
```

Find easily the most suitable templates for your use case.

You can search by:

  * `query::Symbol` which looks look only for partial matches in the template `name`
  * `query::AbstractString` which looks for partial matches in the template `name` or `description`
  * `query::Regex` which looks for matches in the template `name`, `description` or any of the message previews

# Keyword Arguments

  * `limit::Int` limits the number of returned templates (Defaults to 10)

# Examples

Find available templates with `aitemplates`:

```julia
tmps = aitemplates("JuliaExpertAsk")
# Will surface one specific template
# 1-element Vector{AITemplateMetadata}:
# PromptingTools.AITemplateMetadata
#   name: Symbol JuliaExpertAsk
#   description: String "For asking questions about Julia language. Placeholders: `ask`"
#   version: String "1"
#   wordcount: Int64 237
#   variables: Array{Symbol}((1,))
#   system_preview: String "You are a world-class Julia language programmer with the knowledge of the latest syntax. Your commun"
#   user_preview: String "# Question

{{ask}}"
#   source: String ""
```

The above gives you a good idea of what the template is about, what placeholders are available, and how much it would cost to use it (=wordcount).

Search for all Julia-related templates:

```julia
tmps = aitemplates("Julia")
# 2-element Vector{AITemplateMetadata}... -> more to come later!
```

If you are on VSCode, you can leverage nice tabular display with `vscodedisplay`:

```julia
using DataFrames
tmps = aitemplates("Julia") |> DataFrame |> vscodedisplay
```

I have my selected template, how do I use it? Just use the "name" in `aigenerate` or `aiclassify`   like you see in the first example!
