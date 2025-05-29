```
dbc_spinner(;kwargs...)
dbc_spinner(children::Any;kwargs...)
dbc_spinner(children_maker::Function;kwargs...)
```

A Spinner component. Render Bootstrap style loading spinners using only CSS.

This component can be used standalone to render a loading spinner, or it can be used like `dash_core_components.Loading` by giving it children. In the latter case the chosen spinner will display while the children are loading. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component.
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `color` (String; optional): Sets the color of the Spinner. Main options are Bootstrap contextual

colors: primary, secondary, success, info, warning, danger, light, dark, body, muted, white-50, black-50. You can also specify any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name)

If not specified will default to text colour.

  * `delay_hide` (Real; optional): When using the spinner as a loading spinner, add a time delay (in ms) to

the spinner being removed to prevent flickering.

  * `delay_show` (Real; optional): When using the spinner as a loading spinner, add a time delay (in ms) to

the spinner being shown after the loading_state is set to true.

  * `fullscreen` (Bool; optional): Boolean that determines if the loading spinner will be displayed

full-screen or not.

  * `fullscreenClassName` (String; optional): **DEPRECATED** - use `fullscreen_class_name` instead.

Often used with CSS to style elements with common properties.

  * `fullscreen_class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `fullscreen_style` (Dict; optional): Defines CSS styles for the container when fullscreen=True.
  * `show_initially` (Bool; optional): Whether the Spinner should show on app start-up before the loading state

has been determined. Default True.

  * `size` (String; optional): The spinner size. Options are 'sm', and 'md'.
  * `spinnerClassName` (String; optional): **DEPRECATED** - use `spinner_class_name` instead.

CSS class names to apply to the spinner.

  * `spinner_class_name` (String; optional): CSS class names to apply to the spinner.
  * `spinner_style` (Dict; optional): Inline CSS styles to apply to the spinner.
  * `type` (String; optional): The type of spinner. Options 'border' and 'grow'. Default 'border'.
