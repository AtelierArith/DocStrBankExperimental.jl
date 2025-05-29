```
dbc_switch(;kwargs...)
```

A Switch component. Checklist is a component that encapsulates several checkboxes. The values and labels of the checklist is specified in the `options` property and the checked items are specified with the `value` property. Each checkbox is rendered as an input / label pair. `Checklist` must be given an `id` to work properly. Keyword arguments:

  * `id` (String; optional): The ID of this component, used to identify dash components in callbacks.

The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

The class of the container (div)

  * `class_name` (String; optional): The class of the container (div)
  * `disabled` (Bool; optional): Disable the Switch.
  * `inputClassName` (String; optional): **DEPRECATED** Use `input_class_name` instead.

The class of the <input> checkbox element

  * `inputStyle` (Dict; optional): **DEPRECATED** Use `input_style` instead.

The style of the <input> checkbox element.

  * `input_class_name` (String; optional): The class of the <input> checkbox element
  * `input_style` (Dict; optional): The style of the <input> checkbox element.
  * `label` (a list of or a singular dash component, string or number; optional): The label of the <input> element
  * `labelClassName` (String; optional): **DEPRECATED** Use `label_class_name` instead.

CSS classes to apply to the <label> element for each item.

  * `labelStyle` (Dict; optional): **DEPRECATED** Use `label_style` instead.

Inline style arguments to apply to the <label> element for each item.

  * `label_class_name` (String; optional): CSS classes to apply to the <label> element for each item.
  * `label_id` (String; optional): The id of the label
  * `label_style` (Dict; optional): Inline style arguments to apply to the <label> element for each item.
  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `name` (String; optional): The name of the control, which is submitted with the form data.
  * `persisted_props` (Array of a value equal to: 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String | Real; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `style` (Dict; optional): The style of the container (div)
  * `value` (Bool; optional): The value of the input.
