```
dcc_confirmdialogprovider(;kwargs...)
dcc_confirmdialogprovider(children::Any, kwargs...)
dcc_confirmdialogprovider(children_maker::Function, kwargs...)
```

A ConfirmDialogProvider component A wrapper component that will display a confirmation dialog when its child component has been clicked on.

For example:

```
dcc.ConfirmDialogProvider(
    html.Button('click me', id='btn'),
    message='Danger - Are you sure you want to continue.'
    id='confirm')
```

  * `children` (Bool | Real | String | Dict | Array; optional): The children to hijack clicks from and display the popup.
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `cancel_n_clicks` (optional): Number of times the popup was canceled.
  * `cancel_n_clicks_timestamp` (optional): Last time the cancel button was clicked.
  * `displayed` (Bool; optional): Is the modal currently displayed.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `message` (String; optional): Message to show in the popup.
  * `submit_n_clicks` (optional): Number of times the submit was clicked
  * `submit_n_clicks_timestamp` (optional): Last time the submit button was clicked.
