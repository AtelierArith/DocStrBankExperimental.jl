factory(widget::Widget, bootstrap_method::TSBootMethod, nWidgets::Signed)

Creates nWidgets using a given bootstrap_method. If a widget of type "Stock" is passed in then the widget factory will use a given bootstrap method to produce n "Stock" widgets. All widgets use first difference.

## Positional Inputs

  * `widget::Widget`: A concrete widget struct. See the Widget documentation for more.
  * `bootstrap_method`: A subtype of TSBootMethod: Stationary, MovingBlock, or CircularBlock.
  * `nWidgets`: The amount of widgets you want widget factory to return.

# Example

```julia
prices = [1,2,5,9,8,10,5,3];
widget = Stock(prices)

list_of_widgets = factory(widget, Stationary, 2)
```
