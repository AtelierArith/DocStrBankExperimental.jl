```
js_attr(x)
```

Julia式をHTML要素の属性値として渡すことができるJavascript式としてレンダリングします。

### 例

```
using StippleUI

quasar(
  :btn__toggle,
  fieldname = :btn_value,
  options = js_attr([opts(label = "Off", value = false), opts(label = "On", value = true)])
)

# "<q-btn-toggle v-model=\"btn_value\" :options=\"[{'value':false,'label':'Off'}, {'value':true,'label':'On'}]\"></q-btn-toggle>"
```
