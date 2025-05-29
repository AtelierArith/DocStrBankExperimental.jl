```
AITemplate
```

AITemplate is a template for a conversation prompt.   This type is merely a container for the template name, which is resolved into a set of messages (=prompt) by `render`.

# Naming Convention

  * Template names should be in CamelCase
  * Follow the format `<Persona>...<Variable>...` where possible, eg, `JudgeIsItTrue`, ``

      * Starting with the Persona (=System prompt), eg, `Judge` = persona is meant to `judge` some provided information
      * Variable to be filled in with context, eg, `It` = placeholder `it`
      * Ending with the variable name is helpful, eg, `JuliaExpertTask` for a persona to be an expert in Julia language and `task` is the placeholder name
  * Ideally, the template name should be self-explanatory, eg, `JudgeIsItTrue` = persona is meant to `judge` some provided information where it is true or false

# Examples

Save time by re-using pre-made templates, just fill in the placeholders with the keyword arguments:

```julia
msg = aigenerate(:JuliaExpertAsk; ask = "How do I add packages?")
```

The above is equivalent to a more verbose version that explicitly uses the dispatch on `AITemplate`:

```julia
msg = aigenerate(AITemplate(:JuliaExpertAsk); ask = "How do I add packages?")
```

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

You can inspect any template by "rendering" it (this is what the LLM will see):

```julia
julia> AITemplate(:JudgeIsItTrue) |> PromptingTools.render
```

See also: `save_template`, `load_template`, `load_templates!` for more advanced use cases (and the corresponding script in `examples/` folder)
