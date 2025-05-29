```
dcc_clipboard(;kwargs...)
```

A Clipboard component The Clipboard component copies text to the clipboard

  * `id` (String; optional): The ID used to identify this component.
  * `className` (String; optional): The class  name of the icon element
  * `content` (String; optional): The text to  be copied to the clipboard if the `target_id` is None.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `n_clicks` (optional): The number of times copy button was clicked
  * `style` (Dict; optional): The icon's styles
  * `target_id` (String | Dict; optional): The id of target component containing text to copy to the clipboard.

The inner text of the `children` prop will be copied to the clipboard.  If none, then the text from the  `value` prop will be copied.

  * `title` (String; optional): The text shown as a tooltip when hovering over the copy icon.
