```
dbc_collapse(;kwargs...)
dbc_collapse(children::Any;kwargs...)
dbc_collapse(children_maker::Function;kwargs...)
```

A Collapse component. Hide or show content with a vertical collapsing animation. Visibility of the children is controlled by the `is_open` prop which can be targetted by callbacks. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component.
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `dimension` (a value equal to: 'height', 'width'; optional): The dimension used when collapsing e.g. height will collapse vertically,

whilst width will collapse horizontally

  * `is_open` (Bool; optional): Whether collapse is currently open.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `navbar` (Bool; optional): Set to True when using a collapse inside a navbar.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
