```
dbc_navbar(;kwargs...)
dbc_navbar(children::Any;kwargs...)
dbc_navbar(children_maker::Function;kwargs...)
```

A Navbar component. The Navbar component can be used to make fully customisable navbars. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `color` (String; optional): Sets the color of the Navbar. Main options are primary, light and dark, default light.

You can also choose one of the other contextual classes provided by Bootstrap (secondary, success, warning, danger, info, white) or any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name)

  * `dark` (Bool; optional): Applies the `navbar-dark` class to the Navbar, causing text in the children

of the Navbar to use light colors for contrast / visibility.

  * `expand` (Bool | String; optional): Specify screen size at which to expand the menu bar, e.g. sm, md, lg etc.
  * `fixed` (String; optional): Fix the navbar's position at the top or bottom of the page, options: top, bottom
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `light` (Bool; optional): Applies the `navbar-light` class to the Navbar, causing text in the children

of the Navbar to use dark colors for contrast / visibility.

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `role` (String; optional): The ARIA role attribute.
  * `sticky` (a value equal to: 'top'; optional): Position the navbar at the top of the viewport, but only after scrolling past it.

A convenience prop for the sticky-top positioning class. Not supported in <= IE11 and other older browsers

With `sticky`, the navbar remains in the viewport when you scroll. By contrast, with `fixed`, the navbar will remain at the top or bottom of the page.  sticky='top'

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tag` (String; optional): HTML tag to use for the Navbar, default 'nav'
