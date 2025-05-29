```
dcc_textarea(;kwargs...)
```

A Textarea component A basic HTML textarea for entering multiline text.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `accessKey` (String; optional): Defines a keyboard shortcut to activate or add focus to the element.
  * `autoFocus` (String; optional): The element should be automatically focused after the page loaded.
  * `className` (String; optional): Often used with CSS to style elements with common properties.
  * `cols` (String; optional): Defines the number of columns in a textarea.
  * `contentEditable` (String | Bool; optional): Indicates whether the element's content is editable.
  * `contextMenu` (String; optional): Defines the ID of a <menu> element which will serve as the element's context menu.
  * `dir` (String; optional): Defines the text direction. Allowed values are ltr (Left-To-Right) or rtl (Right-To-Left)
  * `disabled` (String | Bool; optional): Indicates whether the user can interact with the element.
  * `draggable` ('true', 'false' | Bool; optional): Defines whether the element can be dragged.
  * `form` (String; optional): Indicates the form that is the owner of the element.
  * `hidden` (String; optional): Prevents rendering of given element, while keeping child elements, e.g. script elements, active.
  * `lang` (String; optional): Defines the language used in the element.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `maxLength` (String; optional): Defines the maximum number of characters allowed in the element.
  * `minLength` (String; optional): Defines the minimum number of characters allowed in the element.
  * `n_blur` (optional): Number of times the textarea lost focus.
  * `n_blur_timestamp` (optional): Last time the textarea lost focus.
  * `n_clicks` (optional): Number of times the textarea has been clicked.
  * `n_clicks_timestamp` (optional): Last time the textarea was clicked.
  * `name` (String; optional): Name of the element. For example used by the server to identify the fields in form submits.
  * `persisted_props` (Array of 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` ('local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `placeholder` (String; optional): Provides a hint to the user of what can be entered in the field.
  * `readOnly` (Bool | 'readOnly', 'readonly', 'READONLY'; optional): Indicates whether the element can be edited.

readOnly is an HTML boolean attribute - it is enabled by a boolean or 'readOnly'. Alternative capitalizations `readonly` & `READONLY` are also acccepted.

  * `required` ('required', 'REQUIRED' | Bool; optional): Indicates whether this element is required to fill out or not.

required is an HTML boolean attribute - it is enabled by a boolean or 'required'. Alternative capitalizations `REQUIRED` are also acccepted.

  * `rows` (String; optional): Defines the number of rows in a text area.
  * `spellCheck` ('true', 'false' | Bool; optional): Indicates whether spell checking is allowed for the element.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tabIndex` (String; optional): Overrides the browser's default tab order and follows the one specified instead.
  * `title` (String; optional): Text to be displayed in a tooltip when hovering over the element.
  * `value` (String; optional): The value of the textarea
  * `wrap` (String; optional): Indicates whether the text should be wrapped.
