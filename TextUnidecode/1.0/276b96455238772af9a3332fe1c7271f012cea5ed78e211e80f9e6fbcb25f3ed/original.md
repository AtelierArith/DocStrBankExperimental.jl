Convert non-ascii characters to "good enough" ascii.

```jldoctest
julia> unidecode("南无阿弥陀佛")
"Nan Wu A Mi Tuo Fo"

julia> unidecode("あみだにょらい")
amidaniyorai
```
