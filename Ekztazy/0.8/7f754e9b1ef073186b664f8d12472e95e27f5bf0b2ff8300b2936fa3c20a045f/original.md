Application Command Option. More details [here](https://discord.com/developers/docs/interactions/application-commands#application-command-object-application-command-option-structure).

## Fields

```
value         :: Any
type          :: Optional{Int}
name          :: Optional{String}
description   :: Optional{String}
required      :: Optional{Bool}
min_value     :: Optional{Number}
max_value     :: Optional{Number}
autocomplete  :: Optional{Bool}
choices       :: Optional{Vector{Ekztazy.ApplicationCommandChoice}}
options       :: Optional{Vector{Ekztazy.ApplicationCommandOption}}
channel_types :: Optional{Vector{Int}}
focused       :: Optional{Bool}
```
