```
dbc_navbarsimple(;kwargs...)
dbc_navbarsimple(children::Any;kwargs...)
dbc_navbarsimple(children_maker::Function;kwargs...)
```

A NavbarSimple component. A self-contained navbar ready for use. If you need more customisability try `Navbar` instead. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `brand` (a list of or a singular dash component, string or number; optional): Brand text, to go top left of the navbar.
  * `brand_external_link` (Bool; optional): If true, the browser will treat the brand link as external,

forcing a page refresh at the new location. If false, this just changes the location without triggering a page refresh. Use this if you are observing dcc.Location, for instance. Defaults to true for absolute URLs and false otherwise.

  * `brand_href` (String; optional): Link to attach to brand.
  * `brand_style` (Dict; optional): CSS style options for brand.
  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `color` (String; optional): Sets the color of the NavbarSimple. Main options are primary, light and dark, default light.

You can also choose one of the other contextual classes provided by Bootstrap (secondary, success, warning, danger, info, white) or any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name)

  * `dark` (Bool; optional): Applies the `navbar-dark` class to the NavbarSimple, causing text in the

children of the Navbar to use light colors for contrast / visibility.

  * `expand` (Bool | String; optional): Specify breakpoint at which to expand the menu bar. Options are: 'xs',

'sm', 'md', 'lg', or 'xl'. Below this breakpoint the navbar will collapse and navitems will be placed in a togglable collapse element.

  * `fixed` (String; optional): Fix the navbar's position at the top or bottom of the page, options: top,

bottom

  * `fluid` (Bool; optional): The contents of the Navbar are wrapped in a container, use fluid=True to

make this container fluid, so that in particular, the contents of the navbar fill the available horizontal space.

  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `light` (Bool; optional): Applies the `navbar-light` class to the NavbarSimple, causing text in the

children of the Navbar to use dark colors for contrast / visibility.

  * `links_left` (Bool; optional): Align the navlinks in the navbar to the left. Default: False.
  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `sticky` (String; optional): Stick the navbar to the top or the bottom of the viewport, options: top, bottom

With `sticky`, the navbar remains in the viewport when you scroll. By contrast, with `fixed`, the navbar will remain at the top or bottom of the page.

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
