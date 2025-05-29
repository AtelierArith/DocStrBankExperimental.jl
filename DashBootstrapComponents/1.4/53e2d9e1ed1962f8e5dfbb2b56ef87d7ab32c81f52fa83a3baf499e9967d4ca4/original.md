```
dbc_cardimg(;kwargs...)
dbc_cardimg(children::Any;kwargs...)
dbc_cardimg(children_maker::Function;kwargs...)
```

A CardImg component. Use CardImg to add images to your cards. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `alt` (String; optional): Alternative text in case an image can't be displayed.
  * `bottom` (Bool; optional): Set to True if image is at bottom of card. This will apply the

card-img-bottom class which rounds the bottom corners to match the corners of the card.

  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `key` (String; optional): A unique identifier for the component, used to improve

performance by React.js while rendering components See https://reactjs.org/docs/lists-and-keys.html for more info

  * `loading_state` (optional): Object that holds the loading state object coming from dash-renderer. loading*state has the following type: lists containing elements 'is*loading', 'prop*name', 'component*name'.

Those elements have the following types:

  * `is_loading` (Bool; optional): Determines if the component is loading or not
  * `prop_name` (String; optional): Holds which property is loading
  * `component_name` (String; optional): Holds the name of the component that is loading
  * `src` (String; optional): The URI of the embeddable content.
  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tag` (String; optional): HTML tag to use for the card body, default: div
  * `title` (String; optional): Text to be displayed as a tooltip when hovering
  * `top` (Bool; optional): Set to True if image is at top of card. This will apply the card-img-top

class which rounds the top corners to match the corners of the card.
