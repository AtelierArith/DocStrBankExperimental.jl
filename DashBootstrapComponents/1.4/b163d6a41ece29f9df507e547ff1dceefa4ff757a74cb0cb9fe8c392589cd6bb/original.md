```
dbc_col(;kwargs...)
dbc_col(children::Any;kwargs...)
dbc_col(children_maker::Function;kwargs...)
```

A Col component. Component for creating Bootstrap columns to control the layout of your page.

Use the width argument to specify width, or use the breakpoint arguments (xs, sm, md, lg, xl) to control the width of the columns on different screen sizes to achieve a responsive layout. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `align` (a value equal to: 'start', 'center', 'end', 'stretch', 'baseline'; optional): Set vertical alignment of this column's content in the parent row. Options

are 'start', 'center', 'end', 'stretch', 'baseline'.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `lg` (optional): Specify column behaviour on a large screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `md` (optional): Specify column behaviour on a medium screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `sm` (optional): Specify column behaviour on a small screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `width` (optional): Specify the width of the column. Behind the scenes this sets behaviour at

the xs breakpoint, and will be overriden if xs is specified.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `xl` (optional): Specify column behaviour on an extra large screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `xs` (optional): Specify column behaviour on an extra small screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.

  * `xxl` (optional): Specify column behaviour on an extra extra large screen.

Valid arguments are boolean, an integer in the range 1-12 inclusive, or a dictionary with keys 'offset', 'order', 'size'. See the documentation for more details.
