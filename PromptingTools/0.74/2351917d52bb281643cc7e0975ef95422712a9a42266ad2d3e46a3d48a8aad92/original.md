```
create_template(; user::AbstractString, system::AbstractString="Act as a helpful AI assistant.", 
    load_as::Union{Nothing, Symbol, AbstractString} = nothing)

create_template(system::AbstractString, user::AbstractString, 
    load_as::Union{Nothing, Symbol, AbstractString} = nothing)
```

Creates a simple template with a user and system message. Convenience function to prevent writing `[PT.UserMessage(...), ...]`

# Arguments

  * `system::AbstractString`: The system message. Usually defines the personality, style, instructions, output format, etc.
  * `user::AbstractString`: The user message. Usually defines the input, query, request, etc.
  * `load_as::Union{Nothing, Symbol, AbstractString}`: If provided, loads the template into the `TEMPLATE_STORE` under the provided name `load_as`. If `nothing`, does not load the template.

Use double handlebar placeholders (eg, `{{name}}`) to define variables that can be replaced by the `kwargs` during the AI call (see example).

Returns a vector of `SystemMessage` and UserMessage objects. If `load_as` is provided, it registers the template in the `TEMPLATE_STORE` and `TEMPLATE_METADATA` as well.

# Examples

Let's generate a quick template for a simple conversation (only one placeholder: name)

```julia
# first system message, then user message (or use kwargs)
tpl=PT.create_template("You must speak like a pirate", "Say hi to {{name}}")

## 2-element Vector{PromptingTools.AbstractChatMessage}:
## PromptingTools.SystemMessage("You must speak like a pirate")
##  PromptingTools.UserMessage("Say hi to {{name}}")
```

You can immediately use this template in `ai*` functions:

```julia
aigenerate(tpl; name="Jack Sparrow")
# Output: AIMessage("Arr, me hearty! Best be sending me regards to Captain Jack Sparrow on the salty seas! May his compass always point true to the nearest treasure trove. Yarrr!")
```

If you're interested in saving the template in the template registry, jump to the end of these examples!

If you want to save it in your project folder:

```julia
PT.save_template("templates/GreatingPirate.json", tpl; version="1.0") # optionally, add description
```

It will be saved and accessed under its basename, ie, `GreatingPirate`.

Now you can load it like all the other templates (provide the template directory):

```julia
PT.load_templates!("templates") # it will remember the folder after the first run
# Note: If you save it again, overwrite it, etc., you need to explicitly reload all templates again!
```

You can verify that your template is loaded with a quick search for "pirate":

```julia
aitemplates("pirate")

## 1-element Vector{AITemplateMetadata}:
## PromptingTools.AITemplateMetadata
##   name: Symbol GreatingPirate
##   description: String ""
##   version: String "1.0"
##   wordcount: Int64 46
##   variables: Array{Symbol}((1,))
##   system_preview: String "You must speak like a pirate"
##   user_preview: String "Say hi to {{name}}"
##   source: String ""
```

Now you can use it like any other template (notice it's a symbol, so `:GreatingPirate`):

```julia
aigenerate(:GreatingPirate; name="Jack Sparrow")
# Output: AIMessage("Arr, me hearty! Best be sending me regards to Captain Jack Sparrow on the salty seas! May his compass always point true to the nearest treasure trove. Yarrr!")
```

If you do not need to save this template as a file, but you want to make it accessible in the template store for all `ai*` functions, you can use the `load_as` (= template name) keyword argument:

```julia
# this will not only create the template, but also register it for immediate use
tpl=PT.create_template("You must speak like a pirate", "Say hi to {{name}}"; load_as="GreatingPirate")

# you can now use it like any other template
aiextract(:GreatingPirate; name="Jack Sparrow")
```
