```
dcc_tooltip(;kwargs...)
dcc_tooltip(children::Any, kwargs...)
dcc_tooltip(children_maker::Function, kwargs...)
```

A Tooltip component A tooltip with an absolute position.

  * `children` (a list of or a singular dash component, string or number; optional): The contents of the tooltip
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `background_color` (String; optional): Color of the tooltip background, as a CSS color string.
  * `bbox` (lists containing elements x0, y0, x1, y1   - `x0` (optional)   - `y0` (optional)   - `x1` (optional)   - `y1` (optional); optional): The bounding box coordinates of the item to label, in px relative to

the positioning parent of the Tooltip component.

  * `border_color` (String; optional): Color of the tooltip border, as a CSS color string.
  * `className` (String; optional): The class of the tooltip
  * `direction` ('top', 'right', 'bottom', 'left'; optional): The side of the `bbox` on which the tooltip should open.
  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `loading_text` (String; optional): The text displayed in the tooltip while loading
  * `show` (Bool; optional): Whether to show the tooltip
  * `style` (Dict; optional): The style of the tooltip
  * `targetable` (Bool; optional): Whether the tooltip itself can be targeted by pointer events.

For tooltips triggered by hover events, typically this should be left `false` to avoid the tooltip interfering with those same events.

  * `zindex` (optional): The `z-index` CSS property to assign to the tooltip. Components with

higher values will be displayed on top of components with lower values.
