```
dbc_card(;kwargs...)
dbc_card(children::Any;kwargs...)
dbc_card(children_maker::Function;kwargs...)
```

A Card component. Component for creating Bootstrap cards. Use in conjunction with CardBody, CardImg, CardLink, CardHeader and CardFooter. Can also be used in conjunction with CardColumns, CardDeck, CardGroup for different layout options. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `body` (Bool; optional): Apply the `card-body` class to the card, so that there is no need to also

include a CardBody component in the children of this Card. Default: False

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `color` (String; optional): Card color, options: primary, secondary, success, info, warning, danger,

light, dark or any valid CSS color of your choice (e.g. a hex code, a decimal code or a CSS color name). Default is light.

  * `inverse` (Bool; optional): Invert text colours for use with a darker background.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `outline` (Bool; optional): Apply color styling to just the border of the card.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
