```
dbc_nav(;kwargs...)
dbc_nav(children::Any;kwargs...)
dbc_nav(children_maker::Function;kwargs...)
```

A Nav component. Nav can be used to group together a collection of navigation links. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `card` (Bool; optional): Set to True when using Nav with pills styling inside a CardHeader.
  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `fill` (Bool; optional): Expand the nav items to fill available horizontal space.
  * `horizontal` (a value equal to: 'start', 'center', 'end', 'between', 'around'; optional): Specify the horizontal alignment of the NavItems. Options are 'start',

'center', or 'end'.

  * `justified` (Bool; optional): Expand the nav items to fill available horizontal space, making sure

every nav item has the same width.

  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `navbar` (Bool; optional): Set to True if using Nav in Navbar component. This applies the `navbar-nav`

class to the Nav which uses more lightweight styles to match the parent Navbar better.

  * `navbar_scroll` (Bool; optional): Enable vertical scrolling within the toggleable contents of a collapsed Navbar.
  * `pills` (Bool; optional): Apply pill styling to nav items. Active items will be indicated by a pill.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `vertical` (Bool | String; optional): Stack NavItems vertically. Set to True for a vertical Nav on all screen

sizes, or pass one of the Bootstrap breakpoints ('xs', 'sm', 'md', 'lg', 'xl') for a Nav which is vertical at that breakpoint and above, and horizontal on smaller screens.
