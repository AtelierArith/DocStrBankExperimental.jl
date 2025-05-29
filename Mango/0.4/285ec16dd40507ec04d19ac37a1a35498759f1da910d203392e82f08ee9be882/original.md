```
subscribe_event(role::Role, event_type::Any, event_handler::Any, condition::Function)
```

Subscribe to specific types of events. 

The types of events are determined by the `condition` function (accepting `src` and `event`) and  by the `event_type`.

# Example

```julia
struct MyEvent end
function custom_handler(role::Role, src::Role, event::Any, event_type::Any)
    # do your thing
end
subscribe_event(my_role, MyEvent, custom_handler, (src, event) -> aid(src) == "agent0")
```
