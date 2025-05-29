```
crossbar(x, y, ymin, ymax; kwargs...)
```

Draw a crossbar. A crossbar represents a range with a (potentially notched) box. It is most commonly used as part of the `boxplot`.

# Arguments

  * `x`: position of the box
  * `y`: position of the midline within the box
  * `ymin`: lower limit of the box
  * `ymax`: upper limit of the box

# Keywords

  * `orientation=:vertical`: orientation of box (`:vertical` or `:horizontal`)
  * `width=0.8`: width of the box
  * `show_notch=false`: draw the notch
  * `notchmin=automatic`: lower limit of the notch
  * `notchmax=automatic`: upper limit of the notch
  * `notchwidth=0.5`: multiplier of `width` for narrowest width of notch
  * `show_midline=true`: show midline
