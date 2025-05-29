```
dcc_location(;kwargs...)
```

A Location component Update and track the current window.location object through the window.history state. Use in conjunction with the `dash_core_components.Link` component to make apps with multiple pages.

  * `id` (String; required): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `hash` (String; optional): hash in window.location - e.g., "#myhash"
  * `href` (String; optional): href in window.location - e.g., "/my/full/pathname?myargument=1#myhash"
  * `pathname` (String; optional): pathname in window.location - e.g., "/my/full/pathname"
  * `refresh` ('callback-nav' | Bool; optional): Use `True` to navigate outside the Dash app or to manually refresh a page.

Use `False` if the same callback that updates the Location component is also updating the page content - typically used in multi-page apps that do not use Pages. Use 'callback-nav' if you are updating the URL in a callback, or a different callback will respond to the new Location with updated content. This is typical with multi-page apps that use Pages. This will allow for navigating to a new page without refreshing the page.

  * `search` (String; optional): search in window.location - e.g., "?myargument=1"
