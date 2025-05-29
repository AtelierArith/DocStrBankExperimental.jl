```
words(languages...; all)
```

List the words in a language as a sorted `Vector{String}`.

The lists are incomplete and their exact contents are subject to change. Setting `all=true` will make an effort to include all words, but at the cost of including some non-words.

Languages can be queried by iso code, name, or english name and are not case sensitive.

The following languages are currently supported:

  * English: "english", "eng", "en"
  * Spanish: "spanish", "español", "spa", "es"
  * Portuguese: "portuguese", "português", "por", "pt"
  * French: "french", "français", "fre", "fr"
  * Italian: "italian", "italiano", "ita", "it"
  * German: "german", "deutsch", "deu", "de"
  * Dutch: "dutch", "nederlands", "nld", "nl"

Multilingual lists are supported. For example, `words("english", "spanish")` will return a sorted list containing words from both English and Spanish.

# Examples

```julia-repl
julia> words("english")
257874-element Vector{String}:
 "Aani"
 "Aaron"
 "Aaronic"
 ⋮
 "zymurgy"
 "zythem"
 "zythum"

julia> words("es", "en")
257874-element Vector{String}:
 "Aani"
 "Aaron"
 "Aaronic"
 ⋮
 "útero"
 "útil"
 "útiles"

julia> rand(words("EnGLiSH", "EspañoL"; all=true), 6)
6-element Vector{String}:
 "Upham"
 "asentir"
 "butcher"
 "fireworm"
 "cirrolite"
 "revocable"
```
