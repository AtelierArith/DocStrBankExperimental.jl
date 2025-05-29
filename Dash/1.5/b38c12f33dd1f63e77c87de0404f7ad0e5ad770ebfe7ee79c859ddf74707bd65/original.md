```
dcc_confirmdialog(;kwargs...)
```

A ConfirmDialog component ConfirmDialog is used to display the browser's native "confirm" modal, with an optional message and two buttons ("OK" and "Cancel"). This ConfirmDialog can be used in conjunction with buttons when the user is performing an action that should require an extra step of verification.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `cancel_n_clicks` (optional): Number of times the popup was canceled.
  * `cancel_n_clicks_timestamp` (optional): Last time the cancel button was clicked.
  * `displayed` (Bool; optional): Set to true to send the ConfirmDialog.
  * `message` (String; optional): Message to show in the popup.
  * `submit_n_clicks` (optional): Number of times the submit button was clicked
  * `submit_n_clicks_timestamp` (optional): Last time the submit button was clicked.
