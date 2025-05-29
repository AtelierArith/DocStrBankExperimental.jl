```
dbc_progress(;kwargs...)
dbc_progress(children::Any;kwargs...)
dbc_progress(children_maker::Function;kwargs...)
```

A Progress component.

Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component. Use this to nest progress bars.
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `animated` (Bool; optional): Animate the bar, must have striped set to True to work.
  * `bar` (Bool; optional): Set to True when nesting Progress inside another Progress component to

create a multi-progress bar.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `color` (String; optional): Set color of the progress bar, options: primary, secondary, success,

warning, danger, info or any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name).

  * `hide_label` (Bool; optional): Set to True to hide the label.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `label` (String; optional): Adds a label to the progress bar.
  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `max` (Real; optional): Upper limit for value, default: 100
  * `min` (Real; optional): Lower limit for value, default: 0
  * `striped` (Bool; optional): Use striped progress bar
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `value` (String | Real; optional): Specify progress, value from min to max inclusive.
