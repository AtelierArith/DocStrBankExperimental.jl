```
clean_player_names(player_name::AbstractString; lowercase::Bool = false, convert_lastfirst::Bool = true, use_name_database::Bool = true, convert_to_ascii::Bool = true)
```

Clean up player names for merges. Can convert names to lowercase, swap first/last names, remove diacritics, and also rely on manual overrides as specified by nflverse devs.

# Examples

```julia-repl
julia> clean_player_names("Tom Brady") 
"Tom Brady"

julia> clean_player_names("Melvin Gordon Jr.")
"Melvin Gordon"

julia> clean_player_names("Melvin Gordon Jr.",lowercase = true)
"melvin gordon"

julia> clean_player_names("Alexander Armah")
"Alex Armah"

julia> clean_player_names("Moritz Böhringer")
"Moritz Bohringer"

julia> clean_player_names("Gordon Jr., Melvin", convert_lastfirst = true)
"Melvin Gordon"
```
