```
html_bdo(;kwargs...)
html_bdo(children::Any, kwargs...)
html_bdo(children_maker::Function, kwargs...)
```

A Bdo component Bdo is a wrapper for the <bdo> HTML5 element. For detailed attribute info see: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/bdo

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `accessKey` (String; optional): Keyboard shortcut to activate or add focus to the element.
  * `aria-*` (String; optional): A wildcard aria attribute
  * `className` (String; optional): Often used with CSS to style elements with common properties.
  * `contentEditable` (String; optional): Indicates whether the element's content is editable.
  * `contextMenu` (String; optional): Defines the ID of a <menu> element which will serve as the element's context menu.
  * `data-*` (String; optional): A wildcard data attribute
  * `dir` (String; optional): Defines the text direction. Allowed values are ltr (Left-To-Right) or rtl (Right-To-Left)
  * `disable_n_clicks` (Bool; optional): When True, this will disable the n_clicks prop.  Use this to remove

event listeners that may interfere with screen readers.

  * `draggable` (String; optional): Defines whether the element can be dragged.
  * `hidden` ('hidden', 'HIDDEN' | Bool; optional): Prevents rendering of given element, while keeping child elements, e.g. script elements, active.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `lang` (String; optional): Defines the language used in the element.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `n_clicks` (optional): An integer that represents the number of times

that this element has been clicked on.

  * `n_clicks_timestamp` (optional): An integer that represents the time (in ms since 1970)

at which n_clicks changed. This can be used to tell which button was changed most recently.

  * `role` (String; optional): Defines an explicit role for an element for use by assistive technologies.
  * `spellCheck` (String; optional): Indicates whether spell checking is allowed for the element.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tabIndex` (String; optional): Overrides the browser's default tab order and follows the one specified instead.
  * `title` (String; optional): Text to be displayed in a tooltip when hovering over the element.
