```
dcc_upload(;kwargs...)
dcc_upload(children::Any, kwargs...)
dcc_upload(children_maker::Function, kwargs...)
```

An Upload component Upload components allow your app to accept user-uploaded files via drag'n'drop

  * `children` (a list of or a singular dash component, string or number | String; optional): Contents of the upload component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `accept` (String; optional): Allow specific types of files.

See https://github.com/okonet/attr-accept for more information. Keep in mind that mime type determination is not reliable across platforms. CSV files, for example, are reported as text/plain under macOS but as application/vnd.ms-excel under Windows. In some cases there might not be a mime type set at all. See: https://github.com/react-dropzone/react-dropzone/issues/276

  * `className` (String; optional): HTML class name of the component
  * `className_active` (String; optional): HTML class name of the component while active
  * `className_disabled` (String; optional): HTML class name of the component if disabled
  * `className_reject` (String; optional): HTML class name of the component if rejected
  * `contents` (String | Array of Strings; optional): The contents of the uploaded file as a binary string
  * `disable_click` (Bool; optional): Disallow clicking on the component to open the file dialog
  * `disabled` (Bool; optional): Enable/disable the upload component entirely
  * `filename` (String | Array of Strings; optional): The name of the file(s) that was(were) uploaded.

Note that this does not include the path of the file (for security reasons).

  * `last_modified` (Array of s; optional): The last modified date of the file that was uploaded in unix time

(seconds since 1970).

  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `max_size` (optional): Maximum file size in bytes. If `-1`, then infinite
  * `min_size` (optional): Minimum file size in bytes
  * `multiple` (Bool; optional): Allow dropping multiple files
  * `style` (Dict; optional): CSS styles to apply
  * `style_active` (Dict; optional): CSS styles to apply while active
  * `style_disabled` (Dict; optional): CSS styles if disabled
  * `style_reject` (Dict; optional): CSS styles if rejected
