```
dcc_store(;kwargs...)
```

A Store component Easily keep data on the client side with this component. The data is not inserted in the DOM. Data can be in memory, localStorage or sessionStorage. The data will be kept with the id as key.

  * `id` (String; required): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `clear_data` (Bool; optional): Set to true to remove the data contained in `data_key`.
  * `data` (Dict | Array | String | Bool; optional): The stored data for the id.
  * `modified_timestamp` (optional): The last time the storage was modified.
  * `storage_type` ('local', 'session', 'memory'; optional): The type of the web storage.

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.
