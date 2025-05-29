```
dcc_rangeslider(;kwargs...)
```

A RangeSlider component A double slider with two handles. Used for specifying a range of numerical values.

  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `allowCross` (Bool; optional): allowCross could be set as true to allow those handles to cross.
  * `className` (String; optional): Additional CSS class for the root DOM node
  * `count` (optional): Determine how many ranges to render, and multiple handles

will be rendered (number + 1).

  * `disabled` (Bool; optional): If true, the handles can't be moved.
  * `dots` (Bool; optional): When the step value is greater than 1,

you can set the dots to true if you want to render the slider with dots.

  * `drag_value` (Array of s; optional): The value of the input during a drag
  * `included` (Bool; optional): If the value is true, it means a continuous

value is included. Otherwise, it is an independent value.

  * `loading_state` (lists containing elements is*loading, prop*name, component*name   - `is*loading`(Bool; optional): Determines if the component is loading or not   -`prop*name`(String; optional): Holds which property is loading   -`component*name` (String; optional): Holds the name of the component that is loading; optional): Object that holds the loading state object coming from dash-renderer
  * `marks` (Dict with Strings as keys and values of type String | lists containing elements label, style   - `label` (String; optional)   - `style` (Dict; optional); optional): Marks on the slider.

The key determines the position (a number), and the value determines what will show. If you want to set the style of a specific mark point, the value should be an object which contains style and label properties.

  * `max` (optional): Maximum allowed value of the slider
  * `min` (optional): Minimum allowed value of the slider
  * `persisted_props` (Array of 'value's; optional): Properties whose user interactions will persist after refreshing the

component or the page. Since only `value` is allowed this prop can normally be ignored.

  * `persistence` (Bool | String; optional): Used to allow user interactions in this component to be persisted when

the component - or the page - is refreshed. If `persisted` is truthy and hasn't changed from its previous value, a `value` that the user has changed while using the app will keep that change, as long as the new `value` also matches what was given originally. Used in conjunction with `persistence_type`.

  * `persistence_type` ('local', 'session', 'memory'; optional): Where persisted user changes will be stored:

memory: only kept in memory, reset on page refresh. local: window.localStorage, data is kept after the browser quit. session: window.sessionStorage, data is cleared once the browser quit.

  * `pushable` (Bool; optional): pushable could be set as true to allow pushing of

surrounding handles when moving an handle. When set to a number, the number will be the minimum ensured distance between handles.

  * `step` (optional): Value by which increments or decrements are made
  * `tooltip` (optional):Configuration for tooltips describing the current slider values. tooltip has the following type: lists containing elements always*visible, placement   - `always*visible` (Bool; optional): Determines whether tooltips should always be visible

(as opposed to the default, visible on hover)   - `placement` ('left', 'right', 'top', 'bottom', 'topLeft', 'topRight', 'bottomLeft', 'bottomRight'; optional): Determines the placement of tooltips See https://github.com/react-component/tooltip#api top/bottom{*} sets the *origin* of the tooltip, so e.g. `topLeft` will in reality appear to be on the top right of the handle

  * `updatemode` ('mouseup', 'drag'; optional): Determines when the component should update its `value`

property. If `mouseup` (the default) then the slider will only trigger its value when the user has finished dragging the slider. If `drag`, then the slider will update its value continuously as it is being dragged. Note that for the latter case, the `drag_value` property could be used instead.

  * `value` (Array of s; optional): The value of the input
  * `vertical` (Bool; optional): If true, the slider will be vertical
  * `verticalHeight` (optional): The height, in px, of the slider if it is vertical.
