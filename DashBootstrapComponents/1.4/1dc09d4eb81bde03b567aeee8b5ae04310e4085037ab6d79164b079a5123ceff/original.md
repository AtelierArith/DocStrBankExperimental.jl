```
dbc_modal(;kwargs...)
dbc_modal(children::Any;kwargs...)
dbc_modal(children_maker::Function;kwargs...)
```

A Modal component. Create a toggleable dialog using the Modal component. Toggle the visibility with the `is_open` prop. Keyword arguments:

  * `children` (a list of or a singular dash component, string or number; optional): The children of this component
  * `id` (String; optional): The ID of this component, used to identify dash components

in callbacks. The ID needs to be unique across all of the components in an app.

  * `autoFocus` (Bool; optional): **DEPRECATED** Use `autofocus` instead

```
Puts the focus on the modal when initialized.
```

  * `autofocus` (Bool; optional): Puts the focus on the modal when initialized.
  * `backdrop` (Bool | a value equal to: 'static'; optional): Includes a modal-backdrop element. Alternatively, specify 'static' for a

backdrop which doesn't close the modal on click.

  * `backdropClassName` (String; optional): **DEPRECATED** Use `backdrop_class_name` instead

CSS class to apply to the backdrop.

  * `backdrop_class_name` (String; optional): CSS class to apply to the backdrop.
  * `centered` (Bool; optional): If true, vertically center modal on page.
  * `className` (String; optional): **DEPRECATED** Use `class_name` instead.

Often used with CSS to style elements with common properties.

  * `class_name` (String; optional): Often used with CSS to style elements with common properties.
  * `contentClassName` (String; optional): **DEPRECATED** Use `content_class_name` instead

CSS class to apply to the modal content.

  * `content_class_name` (String; optional): CSS class to apply to the modal content.
  * `fade` (Bool; optional): Set to false for a modal that simply appears rather than fades into view.
  * `fullscreen` (a value equal to: PropTypes.bool, PropTypes.oneOf(['sm-down', 'md-down', 'lg-down', 'xl-down', 'xxl-down']); optional): Renders a fullscreen modal. Specifying a breakpoint will render the modal

as fullscreen below the breakpoint size.

  * `is_open` (Bool; optional): Whether modal is currently open.
  * `keyboard` (Bool; optional): Close the modal when escape key is pressed.
  * `labelledBy` (String; optional): **DEPRECATED** Use `labelledby` instead

The ARIA labelledby attribute

  * `labelledby` (String; optional): The ARIA labelledby attribute
  * `modalClassName` (String; optional): **DEPRECATED** Use `modal_class_name` instead

CSS class to apply to the modal.

  * `modal_class_name` (String; optional): CSS class to apply to the modal.
  * `role` (String; optional): The ARIA role attribute.
  * `scrollable` (Bool; optional): It true, scroll the modal body rather than the entire modal when it is too

long to all fit on the screen.

  * `size` (String; optional): Set the size of the modal. Options sm, lg, xl for small, large or extra

large sized modals, or leave undefined for default size.

  * `style` (Dict; optional): Defines CSS styles which will override styles previously set.
  * `tag` (String; optional): HTML tag to use for the Modal, default: div
  * `zIndex` (Real | String; optional): **DEPRECATED** Use `zindex` instead

Set the z-index of the modal. Default 1050.

  * `zindex` (Real | String; optional): Set the z-index of the modal. Default 1050.
