```
dcc_dropdown(;kwargs...)
```

A Dropdown component Dropdown is an interactive dropdown element for selecting one or more items. The values and labels of the dropdown items are specified in the `options` property and the selected item(s) are specified with the `value` property.

Use a dropdown when you have many options (more than 5) or when you are constrained for space. Otherwise, you can use RadioItems or a Checklist, which have the benefit of showing the users all of the items at once.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): className of the dropdown element
  * `clearable` (Bool; optional): Whether or not the dropdown is "clearable", that is, whether or

not a small "x" appears on the right of the dropdown that removes the selected value.

  * `disabled` (Bool; optional): If true, this dropdown is disabled and the selection cannot be changed.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `maxHeight` (optional): height of the options dropdown.
  * `multi` (Bool; optional): If true, the user can select multiple values
  * `optionHeight` (optional): height of each option. Can be increased when label lengths would wrap around
  * `options` (optional):An array of options {label: [string|number], value: [string|number]},

an optional disabled field can be used for each option. options has the following type: Array of String | Bools | Dict | Array of lists containing elements label, value, disabled, title, search   - `label` (a list of or a singular dash component, string or number; required): The option's label   - `value` (String | Bool; required): The value of the option. This value corresponds to the items specified in the `value` property.   - `disabled` (Bool; optional): If true, this option is disabled and cannot be selected.   - `title` (String; optional): The HTML 'title' attribute for the option. Allows for information on hover. For more information on this attribute, see https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/title   - `search` (String; optional): Optional search value for the option, to use if the label is a component or provide a custom search value different from the label. If no search value and the label is a component, the `value` will be used for search.s

  * `persisted_props` (Array of 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` ('local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `placeholder` (String; optional): The grey, default text shown when no option is selected
  * `search_value` (String; optional): The value typed in the DropDown for searching.
  * `searchable` (Bool; optional): Whether to enable the searching feature or not
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `value` (String | Bool | Array of String | Bools; optional): The value of the input. If `multi` is false (the default)

then value is just a string that corresponds to the values provided in the `options` property. If `multi` is true, then multiple values can be selected at once, and `value` is an array of items with values corresponding to those in the `options` prop.
