```
html_form(;kwargs...)
html_form(children::Any, kwargs...)
html_form(children_maker::Function, kwargs...)
```

A Form component Form is a wrapper for the <form> HTML5 element. For detailed attribute info see: https://developer.mozilla.org/en-US/docs/Web/HTML/Element/form

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `accept` (String; optional): List of types the server accepts, typically a file type.
  * `acceptCharset` (String; optional): List of supported charsets.
  * `accessKey` (String; optional): Keyboard shortcut to activate or add focus to the element.
  * `action` (String; optional): The URI of a program that processes the information submitted via the form.
  * `aria-*` (String; optional): A wildcard aria attribute
  * `autoComplete` (String; optional): Indicates whether controls in this form can by default have their values automatically completed by the browser.
  * `className` (String; optional): Often used with CSS to style elements with common properties.
  * `contentEditable` (String; optional): Indicates whether the element's content is editable.
  * `contextMenu` (String; optional): Defines the ID of a <menu> element which will serve as the element's context menu.
  * `data-*` (String; optional): A wildcard data attribute
  * `dir` (String; optional): Defines the text direction. Allowed values are ltr (Left-To-Right) or rtl (Right-To-Left)
  * `disable_n_clicks` (Bool; optional): When True, this will disable the n_clicks prop.  Use this to remove

event listeners that may interfere with screen readers.

  * `draggable` (String; optional): Defines whether the element can be dragged.
  * `encType` (String; optional): Defines the content type of the form data when the method is POST.
  * `hidden` ('hidden', 'HIDDEN' | Bool; optional): Prevents rendering of given element, while keeping child elements, e.g. script elements, active.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `lang` (String; optional): Defines the language used in the element.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `method` (String; optional): Defines which HTTP method to use when submitting the form. Can be GET (default) or POST.
  * `n_clicks` (optional): An integer that represents the number of times

that this element has been clicked on.

  * `n_clicks_timestamp` (optional): An integer that represents the time (in ms since 1970)

at which n_clicks changed. This can be used to tell which button was changed most recently.

  * `name` (String; optional): Name of the element. For example used by the server to identify the fields in form submits.
  * `noValidate` ('noValidate', 'novalidate', 'NOVALIDATE' | Bool; optional): This attribute indicates that the form shouldn't be validated when submitted.
  * `role` (String; optional): Defines an explicit role for an element for use by assistive technologies.
  * `spellCheck` (String; optional): Indicates whether spell checking is allowed for the element.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tabIndex` (String; optional): Overrides the browser's default tab order and follows the one specified instead.
  * `target` (String; optional): Specifies where to open the linked document (in the case of an <a> element) or where to display the response received (in the case of a <form> element)
  * `title` (String; optional): Text to be displayed in a tooltip when hovering over the element.
