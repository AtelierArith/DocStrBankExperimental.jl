```
dbc_fade(;kwargs...)
dbc_fade(children::Any;kwargs...)
dbc_fade(children_maker::Function;kwargs...)
```

A Fade component. Hide or show content with a fading animation. Visibility of the children is controlled by the `is_open` prop which can be targetted by callbacks. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `appear` (Bool; optional): Show fade-in animation on initial page load. Default: True.
  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `enter` (Bool; optional): Enable or disable enter transitions. Default: True.
  * `exit` (Bool; optional): Enable or disable exit transitions. Default: True.
  * `is_in` (Bool; optional): Controls whether the children of the Fade component are currently visible

or not.

  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tag` (String; optional): HTML tag to use for the fade component. Default: div.
  * `timeout` (optional): The duration of the transition, in milliseconds.

You may specify a single timeout for all transitions like: `timeout=500` or individually like: timeout={'enter': 300, 'exit': 500}. timeout has the following type: Real | lists containing elements 'enter', 'exit'. Those elements have the following types:

  * `enter` (Real; optional)
  * `exit` (Real; optional)
