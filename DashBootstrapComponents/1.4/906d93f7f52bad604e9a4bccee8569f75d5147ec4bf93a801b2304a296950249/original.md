```
dbc_accordion(;kwargs...)
dbc_accordion(children::Any;kwargs...)
dbc_accordion(children_maker::Function;kwargs...)
```

An Accordion component. A self contained Accordion component. Build up the children using the AccordionItem component. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `active_item` (String | Array of Strings; optional): The item*id of the currently active item. If item*id has not been specified

for the active item, this will default to item-i, where i is the index (starting from 0) of the item.

If `always_open=True`, this needs to be a list of string IDs.

  * `always_open` (Bool; optional): You can make accordion items stay open when another item is opened by

using the always_open prop.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `flush` (Bool; optional): Renders accordion edge-to-edge with its parent container
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `persisted_props` (Array of a value equal to: 'active_item's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String | Real; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `start_collapsed` (Bool; optional): Set to True for all items to be collapsed initially.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
