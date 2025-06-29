```
dbc_checklist(;kwargs...)
```

A Checklist component. Checklist is a component that encapsulates several checkboxes. The values and labels of the checklist is specified in the `options` property and the checked items are specified with the `value` property. Each checkbox is rendered as an input / label pair. `Checklist` must be given an `id` to work properly. Keyword arguments:

  * `id` (String; optional): The ID of this component, used to identify dash components in callbacks.

The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

The class of the container (div)

  * `class_name` (String; optional): The class of the container (div)
  * `inline` (Bool; optional): Arrange Checklist inline
  * `inputCheckedClassName` (String; optional): **DEPRECATED** Use `input_checked_class_name` instead.

Additional CSS classes to apply to the <input> element when the corresponding checkbox is checked.

  * `inputCheckedStyle` (Dict; optional): **DEPRECATED** Use `input_checked_style` instead.

Additional inline style arguments to apply to <input> elements on checked items.

  * `inputClassName` (String; optional): **DEPRECATED** Use `input_class_name` instead.

The class of the <input> checkbox element

  * `inputStyle` (Dict; optional): **DEPRECATED** Use `input_style` instead.

The style of the <input> checkbox element.

  * `input_checked_class_name` (String; optional): Additional CSS classes to apply to the <input> element when the

corresponding checkbox is checked.

  * `input_checked_style` (Dict; optional): Additional inline style arguments to apply to <input> elements on checked

items.

  * `input_class_name` (String; optional): The class of the <input> checkbox element
  * `input_style` (Dict; optional): The style of the <input> checkbox element.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `labelCheckedClassName` (String; optional): **DEPRECATED** Use `label_checked_class_name` instead.

Additional CSS classes to apply to the <label> element when the corresponding checkbox is checked.

  * `labelCheckedStyle` (Dict; optional): **DEPRECATED** Use `label_checked_style` instead.

Additional inline style arguments to apply to <label> elements on checked items.

  * `labelClassName` (String; optional): **DEPRECATED** Use `label_class_name` instead.

CSS classes to apply to the <label> element for each item.

  * `labelStyle` (Dict; optional): **DEPRECATED** Use `label_style` instead.

Inline style arguments to apply to the <label> element for each item.

  * `label_checked_class_name` (String; optional): Additional CSS classes to apply to the <label> element when the

corresponding checkbox is checked.

  * `label_checked_style` (Dict; optional): Additional inline style arguments to apply to <label> elements on checked

items.

  * `label_class_name` (String; optional): CSS classes to apply to the <label> element for each item.
  * `label_style` (Dict; optional): Inline style arguments to apply to the <label> element for each item.
  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `name` (String; optional): The name of the control, which is submitted with the form data.
  * `options` (optional): The options to display as items in the component. This can be an array

or a dictionary as follows:

1. Array of options where the label and the value are the same thing -

[string|number]

2. An array of options

```
{
  "label": [string|number],
  "value": [string|number],
  "disabled": [bool] (Optional),
  "input_id": [string] (Optional),
  "label_id": [string] (Optional)
}
```

3. Simpler `options` representation in dictionary format. The order is not

guaranteed. All values and labels will be treated as strings.

```
{"value1": "label1", "value2": "label2", ... }
```

which is equal to

```
[
  {"label": "label1", "value": "value1"},
  {"label": "label2", "value": "value2"}, ...
]
```

. options has the following type: Array of String | Reals | Dict | Array of lists containing elements 'label', 'value', 'disabled', 'input*id', 'label*id'. Those elements have the following types:

  * `label` (a list of or a singular dash component, string or number; required): The checkbox's label
  * `value` (String | Real; required): The value of the checkbox. This value corresponds to the items

specified in the `value` property.

  * `disabled` (Bool; optional): If true, this checkbox is disabled and can't be clicked on.
  * `input_id` (String; optional): id for this option's input, can be used to attach tooltips or apply

CSS styles

  * `label_id` (String; optional): id for this option's label, can be used to attach tooltips or apply

CSS styless

  * `persisted_props` (Array of a value equal to: 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String | Real; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` (a value equal to: 'local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `style` (Dict; optional): The style of the container (div)
  * `switch` (Bool; optional): Set to True to render toggle-like switches instead of checkboxes.
  * `value` (Array of String | Reals; optional): The currently selected value
