```
dcc_checklist(;kwargs...)
```

A Checklist component Checklist is a component that encapsulates several checkboxes. The values and labels of the checklist are specified in the `options` property and the checked items are specified with the `value` property. Each checkbox is rendered as an input with a surrounding label.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): The class of the container (div)
  * `inline` (Bool; optional): Indicates whether the options labels should be displayed inline (true=horizontal)

or in a block (false=vertical).

  * `inputClassName` (String; optional): The class of the <input> checkbox element
  * `inputStyle` (Dict; optional): The style of the <input> checkbox element
  * `labelClassName` (String; optional): The class of the <label> that wraps the checkbox input

and the option's label

  * `labelStyle` (Dict; optional): The style of the <label> that wraps the checkbox input

and the option's label

  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `options` (optional):An array of options. options has the following type: Array of String | Bools | Dict | Array of lists containing elements label, value, disabled, title   - `label` (a list of or a singular dash component, string or number; required): The option's label   - `value` (String | Bool; required): The value of the option. This value

corresponds to the items specified in the `value` property.   - `disabled` (Bool; optional): If true, this option is disabled and cannot be selected.   - `title` (String; optional): The HTML 'title' attribute for the option. Allows for information on hover. For more information on this attribute, see https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/titles

  * `persisted_props` (Array of 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` ('local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `style` (Dict; optional): The style of the container (div)
  * `value` (Array of String | Bools; optional): The currently selected value
