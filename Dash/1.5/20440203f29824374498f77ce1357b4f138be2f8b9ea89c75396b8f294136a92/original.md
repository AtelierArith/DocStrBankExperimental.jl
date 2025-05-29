```
dcc_loading(;kwargs...)
dcc_loading(children::Any, kwargs...)
dcc_loading(children_maker::Function, kwargs...)
```

A Loading component A Loading component that wraps any other component and displays a spinner until the wrapped component has rendered.

  * `children` (Array of a list of or a singular dash component, string or numbers | a list of or a singular dash component, string or number; optional): Array that holds components to render
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): Additional CSS class for the spinner root DOM node
  * `color` (String; optional): Primary colour used for the loading spinners
  * `debug` (Bool; optional): If true, the spinner will display the component*name and prop*name

while loading

  * `fullscreen` (Bool; optional): Boolean that makes the spinner display full-screen
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `parent_className` (String; optional): Additional CSS class for the outermost dcc.Loading parent div DOM node
  * `parent_style` (Dict; optional): Additional CSS styling for the outermost dcc.Loading parent div DOM node
  * `style` (Dict; optional): Additional CSS styling for the spinner root DOM node
  * `type` ('graph', 'cube', 'circle', 'dot', 'default'; optional): Property that determines which spinner to show

one of 'graph', 'cube', 'circle', 'dot', or 'default'.
