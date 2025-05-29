```
dbc_cardlink(;kwargs...)
dbc_cardlink(children::Any;kwargs...)
dbc_cardlink(children_maker::Function;kwargs...)
```

A CardLink component. Use card link to add consistently styled links to your cards. Links can be used like buttons, external links, or internal Dash style links. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `external_link` (Bool; optional): If true, the browser will treat this as an external link,

forcing a page refresh at the new location. If false, this just changes the location without triggering a page refresh. Use this if you are observing dcc.Location, for instance. Defaults to true for absolute URLs and false otherwise.

  * `href` (String; optional): URL of the resource to link to
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `n_clicks` (Real; optional): An integer that represents the number of times

that this element has been clicked on.

  * `n_clicks_timestamp` (Real; optional): An integer that represents the time (in ms since 1970)

at which n_clicks changed. This can be used to tell which button was changed most recently.

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `target` (String; optional): Target attribute to pass on to the link. Only applies to external links.
