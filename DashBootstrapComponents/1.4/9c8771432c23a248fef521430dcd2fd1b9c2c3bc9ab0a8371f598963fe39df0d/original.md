```
dbc_row(;kwargs...)
dbc_row(children::Any;kwargs...)
dbc_row(children_maker::Function;kwargs...)
```

A Row component. Row is one of the core layout components in Bootstrap. Build up your layout as a series of rows of columns. Row has arguments for controlling the vertical and horizontal alignment of its children, as well as the spacing between columns. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `align` (a value equal to: 'start', 'center', 'end', 'stretch', 'baseline'; optional): Set vertical alignment of columns in this row. Options are 'start',

'center', 'end', 'stretch' and 'baseline'.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `justify` (a value equal to: 'start', 'center', 'end', 'around', 'between', 'evenly'; optional): Set horizontal spacing and alignment of columns in this row. Options are

'start', 'center', 'end', 'around' and 'between'.

  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
