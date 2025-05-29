```
js_attr(x)
```

Renders a Julia expression as Javascript Expression that can be passed as an attribute value in html elements.

### Example

```
using StippleUI

quasar(
  :btn__toggle,
  fieldname = :btn_value,
  options = js_attr([opts(label = "Off", value = false), opts(label = "On", value = true)])
)

# "<q-btn-toggle v-model=\"btn_value\" :options=\"[{'value':false,'label':'Off'}, {'value':true,'label':'On'}]\"></q-btn-toggle>"
```
