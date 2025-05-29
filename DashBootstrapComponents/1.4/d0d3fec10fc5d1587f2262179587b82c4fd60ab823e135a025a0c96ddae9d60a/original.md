```
dbc_tabs(;kwargs...)
dbc_tabs(children::Any;kwargs...)
dbc_tabs(children_maker::Function;kwargs...)
```

A Tabs component. Create Bootstrap styled tabs. Use the `active_tab` property to set, or get get the currently active tab in a callback. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `active_tab` (String; optional): The tab*id of the currently active tab. If tab*id has not been specified

for the active tab, this will default to tab-i, where i is the index (starting from 0) of the tab.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `persisted_props` (Array of a value equal to: 'active_tab's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `active_tab` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String | Real; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
