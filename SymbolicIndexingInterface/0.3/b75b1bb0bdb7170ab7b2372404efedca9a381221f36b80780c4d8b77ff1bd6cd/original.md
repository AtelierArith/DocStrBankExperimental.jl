```
is_markovian(indp)
```

Check if an index provider represents a Markovian system. Markovian systems do not require knowledge of past states to simulate. This function is only applicable to index providers for which `is_time_dependent(indp)` returns `true`.

Non-Markovian index providers return [`observed`](@ref) functions with a different signature. All value providers associated with a non-markovian index provider must implement [`get_history_function`](@ref).

Returns `true` by default.
