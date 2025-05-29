```
function client_data(app::T)::String where {T<:ReactiveModel}
```

Defines additional data that will only be visible by the browser.

It is meant to keep volatile data, e.g. form data that needs to pass a validation first. In order to use the data you most probably also want to define [`js_methods`](@ref)

### Example

```julia
import Stipple.client_data
client_data(m::Example) = client_data(client_name = js"null", client_age = js"null", accept = false)
```

will define the additional fields `client_name`, `client_age` and `accept` for the model `Example`. These should, of course, not overlap with existing fields of your model.
