```
dcc_link(;kwargs...)
dcc_link(children::Any, kwargs...)
dcc_link(children_maker::Function, kwargs...)
```

A Link component Link allows you to create a clickable link within a multi-page app.

For links with destinations outside the current app, `html.A` is a better component to use.

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): Often used with CSS to style elements with common properties.
  * `href` (String; required): The URL of a linked resource.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `refresh` (Bool; optional): Controls whether or not the page will refresh when the link is clicked
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `target` (String; optional): Specifies where to open the link reference.
  * `title` (String; optional): Adds the title attribute to your link, which can contain supplementary

information.
