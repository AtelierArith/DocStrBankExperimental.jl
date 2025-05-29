```
dcc_tab(;kwargs...)
dcc_tab(children::Any, kwargs...)
dcc_tab(children_maker::Function, kwargs...)
```

A Tab component Part of dcc.Tabs - this is the child Tab component used to render a tabbed page. Its children will be set as the content of that tab, which if clicked will become visible.

  * `children` (a list of or a singular dash component, string or number; optional): The content of the tab - will only be displayed if this tab is selected
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): Appends a class to the Tab component.
  * `disabled` (Bool; optional): Determines if tab is disabled or not - defaults to false
  * `disabled_className` (String; optional): Appends a class to the Tab component when it is disabled.
  * `disabled_style` (Dict; optional): Overrides the default (inline) styles when disabled
  * `label` (String; optional): The tab's label
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `selected_className` (String; optional): Appends a class to the Tab component when it is selected.
  * `selected_style` (Dict; optional): Overrides the default (inline) styles for the Tab component when it is selected.
  * `style` (Dict; optional): Overrides the default (inline) styles for the Tab component.
  * `value` (String; optional): Value for determining which Tab is currently selected
