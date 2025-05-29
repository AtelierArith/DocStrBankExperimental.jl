get*followers*ids(; kwargs...) Get a Dict object of follower ids from a particular Twitter user. This function will call the API as many times as allowed or until the desired `max_records` is reached, whichever comes first.

# Examples

```julia-repl
julia> get_followers_ids(screen_name = "jack", count = 10_000)
Dict{String,Any} with 6 entries:
  "previous_cursor_str" => "0"
  ...
```
