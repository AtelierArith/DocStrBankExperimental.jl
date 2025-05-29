```
add_event_handler!(fn, m, event)
```

Add an event handler for given model. `event` must be a `Symbol` corresponding to an event. `fn` must be a function callable with the arguments corresponding to that event. Below is a table of events, arguments, and when do they fire.

|                    event | arguments |                                    when does it fire |
| ------------------------:| ---------:| ----------------------------------------------------:|
|           `:model_built` |       `m` |                      Right after model `m` is built. |
|  `:model_about_to_solve` |       `m` |                    Right before model `m` is solved. |
|          `:model_solved` |       `m` |                     Right after model `m` is solved. |
| `:window_about_to_solve` |  `(m, k)` |     Right before window `k` for model `m` is solved. |
|         `:window_solved` |  `(m, k)` |      Right after window `k` for model `m` is solved. |
|         `:window_failed` |  `(m, k)` | Right after window `k` for model `m` fails to solve. |

# Example

```julia
run_spineopt("sqlite:///path-to-input-db", "sqlite:///path-to-output-db") do m
    add_event_handler!(println, m, :model_built)  # Print the model right after it's built
end
```
