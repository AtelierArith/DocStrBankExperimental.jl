```
html_textarea(;kwargs...)
html_textarea(children::Any, kwargs...)
html_textarea(children_maker::Function, kwargs...)
```

A Textarea component Textarea is a wrapper for the <textarea> HTML5 element. For detailed attribute info see: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `accessKey` (String; optional): Keyboard shortcut to activate or add focus to the element.
  * `aria-*` (String; optional): A wildcard aria attribute
  * `autoComplete` (String; optional): Indicates whether controls in this form can by default have their values automatically completed by the browser.
  * `autoFocus` ('autoFocus', 'autofocus', 'AUTOFOCUS' | Bool; optional): The element should be automatically focused after the page loaded.
  * `className` (String; optional): Often used with CSS to style elements with common properties.
  * `cols` (String; optional): Defines the number of columns in a textarea.
  * `contentEditable` (String; optional): Indicates whether the element's content is editable.
  * `contextMenu` (String; optional): Defines the ID of a <menu> element which will serve as the element's context menu.
  * `data-*` (String; optional): A wildcard data attribute
  * `dir` (String; optional): Defines the text direction. Allowed values are ltr (Left-To-Right) or rtl (Right-To-Left)
  * `disable_n_clicks` (Bool; optional): When True, this will disable the n_clicks prop.  Use this to remove

event listeners that may interfere with screen readers.

  * `disabled` ('disabled', 'DISABLED' | Bool; optional): Indicates whether the user can interact with the element.
  * `draggable` (String; optional): Defines whether the element can be dragged.
  * `form` (String; optional): Indicates the form that is the owner of the element.
  * `hidden` ('hidden', 'HIDDEN' | Bool; optional): Prevents rendering of given element, while keeping child elements, e.g. script elements, active.
  * `inputMode` (String; optional): Provides a hint as to the type of data that might be entered by the user while editing the element or its contents. The attribute can be used with form controls (such as the value of textarea elements), or in elements in an editing host (e.g., using contenteditable attribute).
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `lang` (String; optional): Defines the language used in the element.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `maxLength` (String; optional): Defines the maximum number of characters allowed in the element.
  * `minLength` (String; optional): Defines the minimum number of characters allowed in the element.
  * `n_clicks` (optional): An integer that represents the number of times

that this element has been clicked on.

  * `n_clicks_timestamp` (optional): An integer that represents the time (in ms since 1970)

at which n_clicks changed. This can be used to tell which button was changed most recently.

  * `name` (String; optional): Name of the element. For example used by the server to identify the fields in form submits.
  * `placeholder` (String; optional): Provides a hint to the user of what can be entered in the field.
  * `readOnly` (String; optional): Indicates whether the element can be edited.
  * `required` ('required', 'REQUIRED' | Bool; optional): Indicates whether this element is required to fill out or not.
  * `role` (String; optional): Defines an explicit role for an element for use by assistive technologies.
  * `rows` (String; optional): Defines the number of rows in a text area.
  * `spellCheck` (String; optional): Indicates whether spell checking is allowed for the element.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tabIndex` (String; optional): Overrides the browser's default tab order and follows the one specified instead.
  * `title` (String; optional): Text to be displayed in a tooltip when hovering over the element.
  * `wrap` (String; optional): Indicates whether the text should be wrapped.
